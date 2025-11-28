# OpusNode (TailCamp)

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Status](https://img.shields.io/badge/status-in--development-yellow)
![Version](https://img.shields.io/badge/version-0.1.0-orange)

**Technical Sophistication Meets User-Friendly Design**

[🇰🇷 한국어](README.ko.md) | [🇺🇸 English](README.en.md) | [🇯🇵 日本語](README.ja.md)

---

## 📋 Project Information

**Project Type**: AI-Powered Collaborative Learning Platform  
**Platform**: Web Application  
**Architecture**: Full-Stack Modern Web Application

---

## 🚀 Overview

**OpusNode (TailCamp)** is an AI-powered learning platform that transforms fragmented learning resources into personalized learning roadmaps and matches learners with similar goals for collaborative project-based learning. Each user becomes a node in a collaborative network of creation.

### Core Value Propositions

* 🎯 **Personalized Learning Paths**: AI transforms scattered learning materials into structured, personalized curricula
* 👥 **Intelligent Group Matching**: AI matches learners with similar goals and skill levels for effective collaboration
* 🚀 **Project-Based Learning**: Real-world project experience with automatic portfolio generation
* 🤖 **AI-Powered Assessment**: Comprehensive skill level assessment through AI interviews

---

## ✨ Key Features

### 🧠 AI Assessment System
* Interactive AI interview for skill level evaluation
* Real-time analysis with visual progress indicators
* Multi-dimensional scoring (Backend, Frontend, AI/ML, Mobile, DevOps)
* Personalized learning recommendations

### 👥 Smart Group Matching
* AI-powered matching algorithm based on goals, levels, and collaboration styles
* Optimal group size (3-6 members)
* Transparent matching criteria display
* Automatic group formation and management

### 📚 Personalized Curriculum
* Week-by-week learning roadmap
* Prerequisite relationship tracking
* Adaptive learning based on progress
* Content mapping from public resources

### 🛠️ Project Workspace
* Collaborative project management
* Task assignment and role distribution
* GitHub integration with automatic PR analysis
* AI coach chatbot for guidance

### 🎨 Portfolio Generator
* Automatic project summarization
* Technology stack extraction
* Multiple template styles (Minimal, Dev, Dark, Notion Style)
* PDF and web hosting export options

### 📊 Learning Dashboard
* Progress tracking with visual indicators
* Gamification elements (levels, badges, streaks)
* AI task assistant
* Group project status monitoring

---

## 🎯 Project Objectives

* ✅ Implement AI-powered skill assessment system
* ✅ Build intelligent group matching algorithm
* ✅ Create personalized curriculum generator
* ✅ Develop collaborative project workspace
* ✅ Enable automatic portfolio generation
* ✅ Ensure modern, responsive UI/UX
* ✅ Optimize for performance and scalability

---

## 🛠️ Tech Stack

### Frontend
![Next.js](https://img.shields.io/badge/Next.js-14+-black?logo=next.js)
![TypeScript](https://img.shields.io/badge/TypeScript-5.0+-blue?logo=typescript)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-3.0+-38bdf8?logo=tailwind-css)

* **Framework**: Next.js 14+ (App Router)
* **Language**: TypeScript
* **State Management**: Recoil / Zustand
* **Styling**: Tailwind CSS + shadcn/ui
* **Real-time**: Socket.io Client

### Backend
![NestJS](https://img.shields.io/badge/NestJS-10.0+-e0234e?logo=nestjs)
![Node.js](https://img.shields.io/badge/Node.js-20+-339933?logo=node.js)

* **Framework**: NestJS
* **Language**: TypeScript
* **API**: GraphQL (Apollo) + REST
* **Real-time**: Socket.io
* **Task Queue**: Bull (Redis-based)

### AI & Data
![OpenAI](https://img.shields.io/badge/OpenAI-GPT--4-412991?logo=openai)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-15+-336791?logo=postgresql)
![Redis](https://img.shields.io/badge/Redis-7+-dc382d?logo=redis)

* **LLM**: OpenAI GPT-4 / Anthropic Claude 3.5
* **Orchestration**: LangChain / LangGraph
* **Vector DB**: Milvus / Pinecone
* **Database**: PostgreSQL 15+
* **Cache**: Redis 7+

### Infrastructure
![AWS](https://img.shields.io/badge/AWS-S3-232f3e?logo=amazon-aws)
![Docker](https://img.shields.io/badge/Docker-Ready-2496ed?logo=docker)

* **Hosting**: AWS / Vercel
* **File Storage**: AWS S3
* **CI/CD**: GitHub Actions

---

## 🏃 Quick Start

### Prerequisites

* **Node.js** 20+ installed
* **PostgreSQL** 15+ installed
* **Redis** 7+ installed
* **npm** or **yarn** package manager

### Installation & Setup

1. **Clone the Repository**
   ```bash
   git clone <repository-url>
   cd OpusNode
   ```

2. **Install Dependencies**
   ```bash
   # Frontend
   cd frontend
   npm install
   
   # Backend
   cd ../backend
   npm install
   ```

3. **Environment Setup**
   ```bash
   # Copy environment files
   cp .env.example .env
   # Edit .env with your configuration
   ```

4. **Database Setup**
   ```bash
   # Run migrations
   npm run migrate
   ```

5. **Run the Application**
   ```bash
   # Development mode
   npm run dev
   ```

6. **Access the Application**
   ```
   Frontend: http://localhost:3000
   Backend API: http://localhost:4000
   ```

---

## 📁 Project Structure

```
OpusNode/
├── frontend/                 # Next.js frontend application
│   ├── app/                 # App Router pages
│   ├── components/          # React components
│   ├── lib/                 # Utilities and hooks
│   └── public/              # Static assets
├── backend/                 # NestJS backend application
│   ├── src/
│   │   ├── modules/         # Feature modules
│   │   │   ├── assessment/  # AI assessment module
│   │   │   ├── matching/    # Group matching module
│   │   │   ├── curriculum/  # Curriculum generator
│   │   │   ├── projects/    # Project workspace
│   │   │   └── portfolio/   # Portfolio generator
│   │   ├── common/          # Shared utilities
│   │   └── config/          # Configuration
│   └── test/                # Test files
├── ai-engine/               # AI service layer
│   ├── assessment/          # Assessment engine
│   ├── matching/            # Matching algorithm
│   └── curriculum/          # Curriculum generator
├── docs/                    # Documentation
│   └── plans/               # Design plans and PRD
└── README.md                # This file
```

---

## 🎨 Design System

OpusNode features a comprehensive design system built with modern principles:

* 🎯 **Component-Based Architecture**: Reusable UI components
* 🌈 **Design Tokens**: Consistent color palette and typography
* 📱 **Responsive Design**: Mobile-first approach
* ♿ **Accessibility**: WCAG 2.1 AA compliant
* 🎭 **Dark Mode**: Complete theme support
* ⚡ **Performance**: Optimized animations and loading states

---

## 📚 Documentation

| Language | Documentation | Description |
|----------|--------------|-------------|
| 🇰🇷 | [한국어](README.ko.md) | Full documentation in Korean |
| 🇺🇸 | [English](README.en.md) | Full documentation in English |
| 🇯🇵 | [日本語](README.ja.md) | Full documentation in Japanese |

### Additional Resources

* [Product Requirements Document](docs/plans/TailCamp_PRD.md) - Comprehensive PRD
* Design System - Visual design guidelines (Coming Soon)
* API Documentation - API endpoints reference (Coming Soon)
* Development Guide - Development setup and guidelines (Coming Soon)

---

## 🗓️ Development Roadmap

### Phase 1: MVP (Months 1-3)
* ✅ AI Interview & Assessment System
* ✅ Group Matching Algorithm
* ✅ Learning Dashboard
* ✅ Basic Project Workspace

### Phase 2: Enhancement (Months 4-6)
* 🔄 Project Workspace (Full Features)
* 🔄 AI Coach Chatbot
* 🔄 Portfolio Generator
* 🔄 Gamification Elements

### Phase 3: Scale (Months 7-12)
* 📋 Advanced AI Features
* 📋 Mobile App (Optional)
* 📋 Community Features
* 📋 Premium Features

---

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

---

**Built with ❤️ for Learners**

*A modular learning platform where each user becomes a node in a collaborative network of creation.*


