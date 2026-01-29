<template>
  <section id="projects" class="projects-section container">
    <div class="header-group">
      <h3>Featured Projects</h3>
      <div class="connector-line"></div>
    </div>

    <!-- Carousel Container -->
    <div class="carousel-wrapper">
      <button class="nav-btn prev" @click="prev" aria-label="Previous Project">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
          <polyline points="15 18 9 12 15 6"></polyline>
        </svg>
      </button>

      <div class="carousel-viewport" ref="viewport">
        <div class="carousel-track" :style="trackStyle" @transitionend="handleTransitionEnd">
          <div
            v-for="(project, index) in extendedProjects"
            :key="`${index}-${project.title}`"
            class="project-card"
            :class="{ active: index === activeIndex }"
            @click="selectProject(index)"
          >
            <div class="card-image-wrapper">
               <img v-if="project.image" :src="project.image" :alt="project.title" class="project-image" loading="lazy" />
               <div v-else class="placeholder-image">
                 <span>{{ project.title.charAt(0) }}</span>
               </div>
            </div>
            
            <div class="card-content">
              <h4 class="card-title">{{ project.title }}</h4>
              <p class="card-summary">{{ project.summary }}</p>

              <!-- Tech Stack Tags -->
              <div class="project-tags">
                <span v-for="(tag, tIdx) in project.tags" :key="tIdx" class="tech-tag">
                  {{ tag }}
                </span>
              </div>
              
              <div class="card-actions">
                <a :href="project.link" target="_blank" @click.stop class="github-link" title="View Code">
                   <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                     <path d="M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 0 0-.94-2.61c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0 0 20 4.77 5.07 5.07 0 0 0 19.91 1S18.73.65 16 2.48a13.38 13.38 0 0 0-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07 0 0 0 5 4.77a5.44 5.44 0 0 0-1.5 3.78c0 5.42 3.3 6.61 6.44 7A3.37 3.37 0 0 0 9 18.13V22"></path>
                   </svg>
                </a>
                <span class="more-info-hint">Click for Details</span>
              </div>
            </div>
          </div>
        </div>
      </div>

      <button class="nav-btn next" @click="next" aria-label="Next Project">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
          <polyline points="9 18 15 12 9 6"></polyline>
        </svg>
      </button>
    </div>

    <!-- Expanded Modal -->
    <Teleport to="body">
      <Transition name="modal-fade">
        <div v-if="selectedProjectData" class="project-modal-backdrop" @click="closeModal">
          <div class="project-modal-content" @click.stop>
            <button class="close-modal-btn" @click="closeModal">
               <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                 <line x1="18" y1="6" x2="6" y2="18"></line>
                 <line x1="6" y1="6" x2="18" y2="18"></line>
               </svg>
            </button>
            
            <div class="modal-header">
              <div class="modal-image-placeholder">
                 <span>{{ selectedProjectData.title.charAt(0) }}</span>
              </div>
              <div class="modal-title-group">
                <h3>{{ selectedProjectData.title }}</h3>
                <a :href="selectedProjectData.link" target="_blank" class="modal-github-btn">
                  <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                     <path d="M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 0 0-.94-2.61c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0 0 20 4.77 5.07 5.07 0 0 0 19.91 1S18.73.65 16 2.48a13.38 13.38 0 0 0-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07 0 0 0 5 4.77a5.44 5.44 0 0 0-1.5 3.78c0 5.42 3.3 6.61 6.44 7A3.37 3.37 0 0 0 9 18.13V22"></path>
                   </svg>
                   View Source
                </a>
              </div>
            </div>
            
            <div class="modal-body">
              <p class="modal-summary">{{ selectedProjectData.summary }}</p>
              
              <div class="modal-details">
                <h4>Key Features</h4>
                <ul>
                  <li v-for="(point, idx) in selectedProjectData.details" :key="idx">
                    {{ point }}
                  </li>
                </ul>
              </div>
            </div>
          </div>
        </div>
      </Transition>
    </Teleport>
  </section>
</template>

<script setup>
import { ref, computed, onMounted, onUnmounted } from 'vue'
import deepfakeImg from '@/assets/img/deepfake.webp'
import aiRoboticsImg from '@/assets/img/ai-robotics.png'
import multimodalNewsImg from '@/assets/img/multimodal-news.png'


import dtiImg from '@/assets/img/dti.png'
import indoorImg from '@/assets/img/indoor.png'
import summarizerImg from '@/assets/img/summarizer.png'
import gpuAcceleratedImg from '@/assets/img/gpu-accelerated.jpg'
import logisticImg from '@/assets/img/logistic.png'
import oskiImg from '@/assets/img/oski.png'
import speechToEmotionImg from '@/assets/img/speech-to-emotion.png'
import sjsuVaImg from '@/assets/img/sjsu-va.png'

const projects = [
  {
    title: 'Deepfake Audio Detection',
    summary: 'Retrieval-augmented framework detecting AI-generated deepfake audio with high accuracy using authentic and spoofed comparison samples.',
    link: 'https://github.com/AvinashSaxena777/RADAD-RetrievalAugmentedDeepfakeAudioDetection',
    image: deepfakeImg,
    tags: ['Audio Analysis', 'ML Pipeline', 'Deepfake Detection'],
    details: [
      'Addressed the challenge of detecting AI-generated audio deepfakes by designing a retrieval-augmented detection framework that compares incoming audio against known authentic and spoofed samples.',
      'Built and evaluated a machine-learning pipeline that improved robustness to unseen speakers and new synthesis techniques, achieving strong accuracy in realistic, open-set testing scenarios.',
      'Validated and documented results through extensive experiments and committee review, producing a lightweight, deployment-ready solution suitable for real-world audio forensics use cases.'
    ]
  },
  {
    title: 'Multi-Modal News Recommender',
    summary: 'Multi-modal engine using ViT and BERT for personalized news recommendations with 200ms latency.',
    link: 'https://github.com/AvinashSaxena777/GAT-NRMS-NewsRecommender-CMPE256',
    image: multimodalNewsImg,
    tags: ['Recommendation System', 'ViT & BERT', 'AWS Sagemaker'],
    details: [
      'Developed multi-modal recommendation engine combining image analysis (ViT) and text processing (BERT), achieving 85% accuracy through cross-modal attention mechanisms and knowledge graph integration.',
      'Implemented hybrid neural collaborative filtering with curriculum learning strategy, reducing cold-start issues by 40% through progressive data exposure and synthetic user embedding generation.',
      'Containerized full-stack solution using Docker and deployed on AWS Sagemaker with CI/CD pipelines, achieving 200ms inference latency for large-scale personalized recommendations.'
    ]
  },
  {
    title: 'SJSU Education Assistant',
    summary: 'Agentic RAG virtual assistant using smolagents, LiteLLM, and multi-modal search to solve student queries autonomously.',
    link: 'https://github.com/AvinashSaxena777/CMPE259-NLPFinalProject-EducationAssitantVA',
    image: sjsuVaImg,
    tags: ['Agentic RAG', 'Multi-modal Search', 'LLMs'],
    details: [
      'Architected an Agentic RAG system using smolagents and LiteLLM, enabling a virtual assistant to autonomously solve complex student queries by orchestrating multiple tools, including SQL databases, vector stores, and real-time web searches.',
      'Developed a hybrid retrieval pipeline integrating ChromaDB for semantic similarity search of university policies and a SQLAlchemy backend to query structured data such as professor office hours, assignment deadlines, and course schedules.',
      'Engineered multi-modal search capabilities by integrating a DuckDuckGoSearchTool and a custom VisitWebpageTool to fetch and summarize real-time academic resources, converting live HTML content into clean Markdown for LLM processing.',
      'Implemented a robust data ingestion layer using LangChain and RecursiveCharacterTextSplitter, supporting dynamic document uploads (PDF/TXT) and utilizing HuggingFaceEmbeddings (all-MiniLM-L6-v2) to maintain an up-to-date academic knowledge base.'
    ]
  },
  {
    title: 'DTI Feature Fusion',
    summary: 'Deep learning model (MAGNET-DTI) integrating GATs and MHSA to predict drug-target interactions with 0.969 AUC.',
    link: 'https://github.com/AvinashSaxena777/CMPE252-MagnetDTI-DrugTargetInteraction',
    image: dtiImg,
    tags: ['Bioinformatics', 'Graph Attention', 'Deep Learning'],
    details: [
      'Developed MAGNET-DTI, a deep learning model, achieving high AUC (0.969) and AUPR (0.964) in predicting drug-target interactions by integrating GATs and MHSA.',
      'Engineered a Streamlit web application enabling real-time drug-target interaction predictions and data visualization using drug SMILES and protein sequences.',
      'Fused multi-source drug and target data (physicochemical properties, ESM embeddings) to enhance feature extraction and DTI prediction accuracy, improving drug discovery processes.',
      'Devised a novel approach by combining Multi Head Self Attention and Graph Attention Transformer layer for Drug Target Interaction.'
    ]
  },
  {
    title: 'Indoor Scene Classification',
    summary: 'ResNet50d-based indoor scene classifier using PyTorch/TIMM, achieving 17% accuracy gain via CutMix/Mixup.',
    link: 'https://github.com/AvinashSaxena777/IndoorSceneRecognitionPytorchTIMM',
    image: indoorImg,
    tags: ['Computer Vision', 'PyTorch', 'Data Augmentation'],
    details: [
      'Developed a deep learning model achieving 81.0% accuracy on indoor scene classification across 67 categories, using PyTorch and TIMM libraries with a ResNet50d architecture.',
      'Implemented advanced data augmentation techniques (Mixup and CutMix) and optimized learning strategies, resulting in a 17.33% improvement in test accuracy compared to the baseline model.',
      'Optimized model inference by exporting to ONNX format, reducing GPU inference time by 28.83% (from 115.92ms to 82.50ms) when examined against OpenVINO runtime.'
    ]
  },
  {
    title: 'Oskibot (UC Berkeley Chatbot)',
    summary: 'RAG-based chatbot for UC Berkeley utilizing Amazon Titan, Pinecone, and Langchain for 90% higher relevance.',
    link: 'https://github.com/AvinashSaxena777/OskiBot',
    image: oskiImg,
    tags: ['RAG Chatbot', 'Langchain', 'AWS Bedrock'],
    details: [
      'Implemented a RAG based chatbot for UC Berkeley, using Scrapy, Multithreading, Asynchronous Programming, Amazon Titan Text Embedding, Pinecone, AWS Bedrock, and Langchain providing 90% more relevant and accurate response as compared to ChatGPT model.',
      'Designed a Retrieval Augmented Generation(RAG) powered Chatbot for UC Berkeley website providing 70% more accurate response as compared to ChatGPT for queries related to UC Berkeley.',
      'Implemented web scraping on the UC Berkeley website asynchronously using Multithreading and Scrapy reducing website parsing time by 80% for producing knowledge base document.',
      'Leveraged Amazon Titan Text Embedding models and integrated Pinecone with AWS Bedrock service to store vector embeddings of the document, reducing the application processing time by 90%.'
    ]
  },
  {
    title: 'GPU-Accelerated ML',
    summary: 'Processed 11M+ records using NVIDIA Rapids and CUDA on A100 GPU, reducing training time by 90%.',
    link: 'https://github.com/AvinashSaxena777/GPU-Accelerated-ML---NvidiaRapids',
    image: gpuAcceleratedImg,
    tags: ['CUDA', 'NVIDIA Rapids', 'High Performance'],
    details: [
      'Processed 11 million records using NVIDIA Rapids and CUDA DataFrame, implementing a GPU-accelerated regressor model with an error rate of 0.015.',
      'Engineered features using GPU-supported libraries for outlier analysis, robust scaling, and text vectorization, improving model performance by 25%.',
      'Experimented with cuml\'s XGBoost, Random Forest, and SGD Regressor models, achieving best results on A100 GPU, reducing training time by 90%.',
      'Employed NVIDIA Rapids and cuDF (GPU Dataframe) for data preprocessing and feature engineering on synthetic generated data consisting of 12 million records.'
    ]
  },
  {
    title: 'Chat Summarizer (LLM)',
    summary: 'Finetuned Hugging Face T5 and BART models on SAMSum dataset for abstractive summarization.',
    link: 'https://github.com/AvinashSaxena777/CMPE258-HW2-samsum-summarizer',
    image: summarizerImg,
    tags: ['LLM Finetuning', 'NLP', 'Hugging Face'],
    details: [
      'Performed Prompt Engineering and Finetuned Hugging Face\'s T5-small and BART-large-CNN on the SAMSum dataset for abstractive summarization, achieving ROUGE-1 scores of approximately 0.416 and 0.4158, respectively.'
    ]
  },
  {
    title: 'CUDA Logistic Regression',
    summary: 'Custom C++/CUDA library for parallelized logistic regression training, speeding up computation by 80%.',
    link: 'https://github.com/AvinashSaxena777/TitanicSurvivalPrecidtion-CUDAProgramming',
    image: logisticImg,
    tags: ['CUDA C++', 'Parallel Computing', 'ML Algorithms'],
    details: [
      'Built Logistic Regression framework for binary and multi-class classification in CUDA programming, handled device synchronization, kernel execution, device and host memory management.',
      'Designed a custom C++ library utilizing CUDA to execute matrix multiplications and compute advanced loss functions leveraging parallel processing for faster computation.'
    ]
  },
  {
    title: 'Speech to Emotion',
    summary: 'Mental wellness app converting speech to emotion using WavLM and Pytorch with 92% accuracy.',
    link: 'https://github.com/AvinashSaxena777/HerokuSpeechToEmotion',
    image: speechToEmotionImg,
    tags: ['Audio Processing', 'WavLM', 'Mental Health AI'],
    details: [
      'Created a mental wellness application to convert speech to emotion, utilizing audio dataset such as RAVDEES and SAVEE on pretrained LLM models via Huggingface API.',
      'Utilized Pytorch framework to administer audio pre-processing, noise filtering and fine-tuning WavLM model improving accuracy by 20 percent, achieving overall accuracy of 92% for detecting user\'s emotion.'
    ]
  },
  {
    title: 'Autonomous Robot Patrolling',
    summary: 'Multi-threat detection system using YOLOv8 and Transformers for autonomous patrolling with 95% accuracy.',
    link: 'https://github.com/AvinashSaxena777/SSRCP-CMPE281',
    image: aiRoboticsImg,
    tags: ['Computer Vision', 'YOLOv8', 'Transformers'],
    details: [
      'Designed multi-threat detection system using YOLOv8 and Transformer models, achieving 95% accuracy through robust evaluation frameworks combining synthetic data augmentation and real-world validation.',
      'Implemented automated quality control pipelines using Carla simulator and gRPC-io integration, reducing false positives by 40% through iterative feedback loops and continuous model refinement.',
      'Architected AWS cloud deployment with Sagemaker endpoints and auto-scaling groups, enabling 50+ concurrent monitoring sessions while maintaining 99.9% uptime for production-grade ML infrastructure.'
    ]
  }
]

// Carousel Logic
const activeIndex = ref(0)
const selectedProjectData = ref(null)
const transitionEnabled = ref(true)

// Create 3 sets for infinite loop illusion
const extendedProjects = computed(() => {
  return [...projects, ...projects, ...projects]
})

// Initialize to the middle set
onMounted(() => {
  activeIndex.value = projects.length
  window.addEventListener('keydown', handleKeydown)
})

const prev = () => {
  activeIndex.value--
}

const next = () => {
  activeIndex.value++
}

const selectProject = (index) => {
  activeIndex.value = index
  selectedProjectData.value = extendedProjects.value[index]
}

const handleTransitionEnd = () => {
  const len = projects.length
  
  // If we are in the first set (too far left), jump to middle set
  if (activeIndex.value < len) {
    transitionEnabled.value = false
    activeIndex.value += len
    // Restore transition after snap
    requestAnimationFrame(() => {
       requestAnimationFrame(() => {
          transitionEnabled.value = true
       })
    })
  } 
  // If we are in the third set (too far right), jump to middle set
  else if (activeIndex.value >= 2 * len) {
    transitionEnabled.value = false
    activeIndex.value -= len
    requestAnimationFrame(() => {
       requestAnimationFrame(() => {
          transitionEnabled.value = true
       })
    })
  }
}

const closeModal = () => {
  selectedProjectData.value = null
}

const trackStyle = computed(() => {
  const stride = 312 // Card width (280) + gap (32)
  return {
    transform: `translateX(calc(50% - 140px - ${activeIndex.value * stride}px))`,
    transition: transitionEnabled.value ? 'transform 0.5s cubic-bezier(0.25, 1, 0.5, 1)' : 'none'
  }
})

// Keyboard navigation
const handleKeydown = (e) => {
  if (selectedProjectData.value) {
    if (e.key === 'Escape') closeModal()
    return
  }
  if (e.key === 'ArrowLeft') prev()
  if (e.key === 'ArrowRight') next()
}

onUnmounted(() => {
  window.removeEventListener('keydown', handleKeydown)
})
</script>

<style scoped>
.projects-section {
  flex-direction: column;
  padding-block: 4rem;
  overflow: hidden; /* Prevent horizontal scrollbar on body */
}

.header-group {
  display: flex;
  align-items: center;
  gap: 2rem;
  margin-bottom: 3rem;
  
  h3 {
    text-transform: uppercase;
    font-size: var(--text-2xl);
    margin: 0;
    white-space: nowrap;
  }
}

.connector-line {
  height: 2px;
  background: linear-gradient(90deg, var(--color-gray-800), transparent);
  width: 100%;
  border-radius: 99px;
}

/* Carousel */
.carousel-wrapper {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 450px;
  perspective: 1000px;
}

.carousel-viewport {
  width: 100%;
  height: 100%;
  overflow: visible; /* Allow seeing neighbors */
  /* Masking is complex with visible overflow, usually we rely on screen edge or fade */
}

.carousel-track {
  display: flex;
  align-items: center;
  gap: 32px; /* 2rem gap */
  height: 100%;
  transition: transform 0.5s cubic-bezier(0.25, 1, 0.5, 1);
  will-change: transform;
  /* Initial alignment handled by Computed Style */
}

/* Controls */
.nav-btn {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  z-index: 10;
  background: rgba(0,0,0,0.5);
  border: 1px solid rgba(255,255,255,0.2);
  color: white;
  width: 48px;
  height: 48px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  backdrop-filter: blur(4px);
  transition: all 0.2s ease;
}

.nav-btn:hover {
  background: var(--color-accent);
  border-color: var(--color-accent);
  color: black;
}

.prev { left: 0; }
.next { right: 0; }

/* Cards */
.project-card {
  width: 280px;
  height: 400px;
  flex-shrink: 0;
  background: var(--color-gray-800);
  border-radius: 12px;
  overflow: hidden;
  position: relative;
  transition: all 0.5s ease;
  cursor: pointer;
  border: 1px solid var(--border-color);
  opacity: 0.5;
  transform: scale(0.9);
  
  /* Netflix-style hover */
  display: flex;
  flex-direction: column;
}

.project-card.active {
  opacity: 1;
  transform: scale(1);
  box-shadow: 0 10px 30px rgba(0,0,0,0.5);
  border-color: var(--color-accent);
  z-index: 5;
}

.project-card:hover {
  border-color: var(--color-accent);
}

.card-image-wrapper {
  height: 160px;
  background: linear-gradient(135deg, var(--color-gray-700), var(--color-gray-800));
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}

.project-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.3s ease;
}

.project-card:hover .project-image {
  transform: scale(1.1);
}

.placeholder-image {
  font-size: 4rem;
  font-weight: 900;
  color: rgba(255,255,255,0.1);
  text-transform: uppercase;
}

.card-content {
  padding: 1.5rem;
  flex: 1;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.card-title {
  font-size: var(--text-lg);
  font-weight: var(--fw-bold);
  line-height: 1.2;
  margin-bottom: 0.5rem;
  color: var(--color-default-white);
}

.card-summary {
  font-size: var(--text-sm);
  color: var(--color-gray-400);
  line-height: 1.4;
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
  margin-bottom: 1rem;
}

.card-actions {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-top: auto;
}

.github-link {
  color: var(--color-gray-300);
  padding: 8px;
  border-radius: 50%;
  background: rgba(255,255,255,0.05);
  transition: all 0.2s ease;
  
  svg {
    width: 20px;
    height: 20px;
  }
}

.github-link:hover {
  background: var(--color-default-white);
  color: var(--color-default-black);
}

.more-info-hint {
  font-size: var(--text-xs);
  color: var(--color-accent);
  font-weight: var(--fw-bold);
  opacity: 0;
  transform: translateX(-10px);
  transition: all 0.3s ease;
}

.project-card:hover .more-info-hint,
.project-card.active .more-info-hint {
  opacity: 1;
  transform: translateX(0);
}

/* Modal */
.project-modal-backdrop {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background: rgba(0,0,0,0.8);
  backdrop-filter: blur(8px);
  z-index: 9999;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 2rem;
}

.project-modal-content {
  background: var(--color-gray-800);
  width: 100%;
  max-width: 800px;
  max-height: 90vh;
  border-radius: 16px;
  overflow-y: auto;
  position: relative;
  box-shadow: 0 25px 50px rgba(0,0,0,0.5);
  border: 1px solid var(--border-color);
  animation: modal-pop 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275);
}

.close-modal-btn {
  position: absolute;
  top: 1rem;
  right: 1rem;
  background: rgba(0,0,0,0.5);
  border: none;
  border-radius: 50%;
  color: white;
  width: 36px;
  height: 36px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  z-index: 10;
  transition: background 0.2s;
  
  svg { width: 20px; height: 20px; }
}

.close-modal-btn:hover {
  background: var(--color-accent);
  color: black;
}

.modal-header {
  height: 250px;
  background: linear-gradient(135deg, var(--color-gray-700), var(--color-gray-900));
  position: relative;
  display: flex;
  align-items: flex-end;
  padding: 2rem;
}

.modal-image-placeholder {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 8rem;
  font-weight: 900;
  color: rgba(255,255,255,0.05);
  overflow: hidden;
  z-index: 0;
}

.modal-title-group {
  position: relative;
  z-index: 1;
  width: 100%;
}

.modal-title-group h3 {
  font-size: var(--text-2xl); /* Fallback */
  font-size: clamp(1.5rem, 4vw, 2.5rem);
  color: white;
  margin-bottom: 1rem;
  text-shadow: 0 2px 4px rgba(0,0,0,0.5);
}

.modal-github-btn {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  background: var(--color-default-white);
  color: var(--color-default-black);
  padding: 0.6rem 1.2rem;
  border-radius: 6px;
  font-weight: var(--fw-bold);
  font-size: var(--text-sm);
  transition: transform 0.2s;
  
  svg { width: 18px; height: 18px; }
}

.modal-github-btn:hover {
  transform: scale(1.05);
  text-decoration: none;
}

.modal-body {
  padding: 2rem;
}

.modal-summary {
  font-size: var(--text-lg);
  color: var(--color-silver-600);
  margin-bottom: 2rem;
  line-height: 1.6;
}

.modal-details h4 {
  color: var(--color-accent);
  margin-bottom: 1rem;
  text-transform: uppercase;
  font-size: var(--text-sm);
  letter-spacing: 1px;
}

.modal-details ul {
  list-style: none;
  padding: 0;
}

.modal-details li {
  position: relative;
  padding-left: 1.5rem;
  margin-bottom: 0.8rem;
  color: var(--paragraph-color);
  line-height: 1.6;
}

.modal-details li::before {
  content: 'details';
  color: transparent; /* A dummy content for sizing if needed or use unicode */
  position: absolute;
  left: 0;
  top: 0;
  width: 6px;
  height: 6px;
  background: var(--color-accent);
  border-radius: 50%;
  margin-top: 10px;
}

/* Transitions */
.modal-fade-enter-active,
.modal-fade-leave-active {
  transition: opacity 0.3s ease;
}

.modal-fade-enter-from,
.modal-fade-leave-to {
  opacity: 0;
}

@keyframes modal-pop {
  0% { transform: scale(0.9) translateY(20px); opacity: 0; }
  100% { transform: scale(1) translateY(0); opacity: 1; }
}

/* Light Mode Overrides */
body[data-theme='light'] {
  & .header-group h3 { color: var(--text-color-default); }
  & .connector-line { background: linear-gradient(90deg, var(--color-gray-300), transparent); }
  
  & .project-card {
    background: var(--color-default-white);
    box-shadow: var(--elevation-2);
  }
  
  & .project-card.active { box-shadow: var(--elevation-4); }
  
  & .card-title { color: var(--color-gray-800); }
  & .card-summary { color: var(--color-gray-600); }
  
  & .card-image-wrapper {
    background: linear-gradient(135deg, var(--color-gray-200), var(--color-gray-300));
  }
  & .placeholder-image { color: rgba(255,255,255,0.4); }
  
  & .github-link {
    background: var(--color-gray-100);
    color: var(--color-gray-700);
  }
  
  & .github-link:hover {
    background: var(--color-gray-800);
    color: white;
  }
  
  /* Modal Light */
  & .project-modal-content {
    background: var(--color-default-white);
  }
  
  & .modal-summary { color: var(--color-gray-600); }
  & .modal-details li { color: var(--color-gray-700); }
  
  & .tech-tag {
    background: var(--color-gray-200);
    border-color: var(--color-gray-400);
    color: var(--color-gray-900); /* Dark text for better readability */
    font-weight: 600;
    font-size: 0.75rem; /* Slightly larger for clarity */
  }

  & .project-card:hover .tech-tag {
    background: var(--color-accent);
    color: var(--color-default-black);
    border-color: var(--color-accent);
  }
}

/* Project Tags */
.project-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-bottom: 1rem;
}

.tech-tag {
  font-size: 0.7rem;
  font-family: var(--font-mono);
  color: var(--color-accent);
  background: rgba(255, 255, 255, 0.08); /* Slightly lighter for contrast */
  padding: 0.25rem 0.6rem;
  border-radius: 6px;
  border: 1px solid rgba(255, 255, 255, 0.1);
  white-space: nowrap;
  letter-spacing: 0.5px;
  transition: all 0.2s ease;
}

.project-card:hover .tech-tag {
  border-color: var(--color-accent);
  background: rgba(26, 188, 209, 0.1); /* Based on accent color usually */
}

/* Responsive */
@media (--vw-md) {
  .carousel-wrapper { height: 400px; }
  .project-card { width: 240px; height: 350px; }
  .card-image-wrapper { height: 130px; }
}

@media (--vw-sm) {
  .carousel-wrapper { 
     perspective: none; 
     height: auto;
     flex-direction: column;
  }
  
  .carousel-viewport {
    height: 380px; /* still need height for transforms */
    width: 100%;
  }
  
  .project-card {
    width: 260px;
    height: 360px;
  }

  .nav-btn {
    top: auto;
    bottom: -60px;
  }
  
  .prev { left: 30%; }
  .next { right: 30%; }
}
</style>
