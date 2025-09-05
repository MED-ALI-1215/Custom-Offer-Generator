# Cybersecurity AI Offer Generator

A sophisticated Flask-based application that leverages AI to generate comprehensive cybersecurity service offers. This system combines document processing, semantic search, and advanced language models to create tailored proposals for cybersecurity solutions.

## Features

### Core Capabilities
- **Intelligent Document Processing**: Automatically extracts and processes PPTX files to build a knowledge base
- **Semantic Search**: Uses FAISS vector database with sentence transformers for relevant document retrieval
- **AI-Powered Generation**: Employs Cohere's Command-R model for professional offer generation
- **Quality Control**: Multi-stage grading system for document relevance, hallucination detection, and answer quality
- **Workflow Orchestration**: LangGraph-based pipeline with intelligent routing and fallback mechanisms

### Advanced Features
- **Comprehensive Metrics**: Performance, quality, and cost tracking with detailed analytics
- **Taxonomy Classification**: Automatic categorization of cybersecurity domains and AI solutions
- **Real-time Monitoring**: Health checks and component testing endpoints
- **LangSmith Integration**: Full tracing and observability for debugging and optimization

## Architecture

### Technology Stack
- **Backend**: Flask with CORS support
- **AI/ML**: LangChain, Cohere API, Sentence Transformers
- **Vector Database**: FAISS for efficient similarity search
- **Document Processing**: python-pptx for PowerPoint extraction
- **Workflow**: LangGraph for complex AI pipelines
- **Monitoring**: LangSmith for tracing and analytics

### Pipeline Components
1. **Router**: Intelligently routes queries between vector search and web fallback
2. **Retriever**: Semantic search through processed documents
3. **Graders**: Multi-layer quality assessment (relevance, hallucination, completeness)
4. **Generator**: Context-aware offer generation with structured output
5. **Metrics**: Comprehensive quality and performance tracking

## Installation

### Prerequisites
- Python 3.8+
- Git
- PowerPoint documents for knowledge base

### Setup
1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd cybersecurity-ai-offer-generator
   ```

2. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Environment Configuration**
   Set the following environment variables:
   ```bash
   export COHERE_API_KEY="your_cohere_api_key"
   export LANGCHAIN_API_KEY="your_langsmith_api_key"
   export LANGCHAIN_TRACING_V2="true"
   export LANGCHAIN_ENDPOINT="https://api.smith.langchain.com"
   export LANGCHAIN_PROJECT="AI_Offer"
   ```

4. **Document Setup**
   Update the `drive_path` variable in `app.py` to point to your PPTX documents directory:
   ```python
   drive_path = r"path/to/your/documents"
   ```

5. **Run the application**
   ```bash
   python app.py
   ```

## API Endpoints

### Core Endpoints
- `GET /` - Main web interface
- `POST /generate` - Generate cybersecurity offers
- `GET /health` - System health and component status
- `GET /test-components` - Individual component testing

### Utility Endpoints
- `GET /taxonomy` - Get taxonomy structure
- `POST /taxonomy/classify` - Classify questions by taxonomy
- `GET /documents/stats` - Document processing statistics

## Usage

### Generating an Offer
Send a POST request to `/generate` with a JSON payload:

```json
{
  "question": "Generate a cybersecurity AI solution for threat detection and incident response"
}
```

The system will return a comprehensive response including:
- Generated offer in French
- Processing pipeline steps
- Quality metrics and scoring
- Performance analytics
- Confidence assessments

### Response Structure
```json
{
  "final_result": "Generated offer content...",
  "steps": [
    {
      "step": "retrieve",
      "status": "completed",
      "description": "Document retrieval...",
      "documents_count": 5
    }
  ],
  "metrics": {
    "processing_time": 2.34,
    "quality": {
      "overall_score": 0.85,
      "grade": "0.85, B"
    },
    "confidence_score": 82,
    "taxonomy": {...}
  }
}
```

## Configuration

### Offer Taxonomy
The system classifies offers into predefined categories:
- **Cybersecurity**: threat_detection, vulnerability_management, compliance, incident_response, identity_management
- **AI Solutions**: machine_learning, nlp, computer_vision, predictive_analytics

### Quality Metrics
The system evaluates generated offers across multiple dimensions:
- **Precision**: Technical term coverage and accuracy
- **Consistency**: Structural quality and readability
- **Completeness**: Required section coverage
- **Relevance**: Alignment with input query

### Performance Monitoring
Comprehensive tracking includes:
- Processing time and memory usage
- Document retrieval effectiveness
- Pipeline efficiency metrics
- Cost estimation and token usage

## Development

### Project Structure
```
├── app.py              # Main Flask application
├── requirements.txt    # Python dependencies
├── templates/          # HTML templates
└── static/            # Static assets
```

### Key Components
- **Document Processing**: PPTX extraction and chunking
- **Embedding System**: Sentence transformer integration
- **Vector Store**: FAISS index management
- **LLM Integration**: Cohere API wrapper
- **Workflow Engine**: LangGraph pipeline
- **Quality Assurance**: Multi-stage grading

### Testing
Use the `/test-components` endpoint to verify:
- Document retrieval functionality
- Router decision making
- Grader performance
- Generation quality
- Workflow execution

## Production Considerations

### Security
- Secure API key management
- Input validation and sanitization
- Rate limiting implementation
- Error handling and logging

### Performance
- Document indexing optimization
- Caching strategies
- Async processing for large requests
- Resource monitoring and alerting

### Scalability
- Database migration from FAISS to production vector DB
- Load balancing and horizontal scaling
- Microservices architecture consideration
- CI/CD pipeline implementation

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/new-feature`)
3. Commit changes (`git commit -am 'Add new feature'`)
4. Push to branch (`git push origin feature/new-feature`)
5. Create Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Support

For issues and questions:
1. Check the `/health` endpoint for system status
2. Use `/test-components` for debugging
3. Review logs for error details
4. Contact the development team

## Changelog

### Version 1.0.0
- Initial release with core functionality
- Document processing and semantic search
- AI-powered offer generation
- Quality control and metrics
- LangSmith integration and monitoring
