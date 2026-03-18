# AWS Serverless API

A production-ready serverless REST API built using AWS Lambda, API Gateway, and DynamoDB. This project demonstrates a fully serverless architecture with automated CI/CD deployment.

## Architecture Overview

```
┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│   Client     │────>│ API Gateway  │────>│ Lambda (API) │
│  (Browser/   │     │  (REST API)  │     │   (Python)   │
│    Mobile)   │     │              │     │              │
└──────────────┘     └──────────────┘     └──────┬───────┘
                                                  │
                                            ┌─────▼─────┐
                                            │  DynamoDB │
                                            │  (NoSQL)  │
                                            │   Table   │
                                            └───────────┘
```

## Features

- **RESTful API** - Full CRUD operations (Create, Read, Update, Delete)
- **Serverless Compute** - AWS Lambda functions with Python runtime
- **NoSQL Database** - Amazon DynamoDB for scalable data storage
- **API Gateway** - REST API with request/response mapping
- **CI/CD Pipeline** - Automated deployment using GitHub Actions
- **Infrastructure as Code** - AWS SAM/CloudFormation templates
- **Monitoring** - CloudWatch logs and metrics

## Tech Stack

| Category       | Technology                          |
|----------------|-------------------------------------|
| Compute        | AWS Lambda (Python 3.x)             |
| API            | AWS API Gateway (REST)              |
| Database       | Amazon DynamoDB                     |
| IaC            | AWS SAM / CloudFormation            |
| CI/CD          | GitHub Actions                      |
| Monitoring     | Amazon CloudWatch                   |
| Auth           | AWS Cognito (optional)              |

## Project Structure

```
aws-serverless-api/
├── src/
│   ├── app.py              # Lambda handler (CRUD operations)
│   ├── requirements.txt    # Python dependencies
│   └── db.py               # DynamoDB interactions
├── templates/
│   └── template.yaml       # AWS SAM template
├── .github/
│   └── workflows/
│       └── deploy.yml      # CI/CD pipeline
├── tests/
│   └── test_api.py         # Unit tests
├── .gitignore
├── README.md
└── LICENSE
```

## API Endpoints

| Method   | Endpoint          | Description              |
|----------|-------------------|--------------------------|
| GET      | /items            | List all items           |
| GET      | /items/{id}       | Get item by ID           |
| POST     | /items            | Create a new item        |
| PUT      | /items/{id}       | Update an existing item  |
| DELETE   | /items/{id}       | Delete an item           |

## Setup & Deployment

### Prerequisites
- AWS Account with CLI configured
- Python 3.x
- AWS SAM CLI
- GitHub account

### Local Development
```bash
# Clone the repository
git clone https://github.com/pogiri-srinivas/aws-serverless-api.git
cd aws-serverless-api

# Install dependencies
pip install -r src/requirements.txt

# Run SAM locally
sam build
sam local start-api
```

### Deploy to AWS
```bash
# Deploy using SAM
sam build
sam deploy --guided
```

## CI/CD Pipeline

The GitHub Actions workflow (`deploy.yml`) automates:
1. Code linting and unit testing on every push
2. Building the SAM application
3. Deploying to AWS on merge to main branch

## Security Best Practices

- IAM roles with least privilege
- API Gateway request validation
- Environment variables for secrets (via AWS Secrets Manager)
- VPC endpoint for private DynamoDB access
- CloudWatch log encryption

## Cost Estimation

| Service       | Monthly Estimate (Free Tier) |
|---------------|------------------------------|
| Lambda        | ~$0 (1M free requests)       |
| API Gateway   | ~$0 (1M free requests)       |
| DynamoDB      | ~$0 (25GB free storage)      |
| CloudWatch    | ~$0 (within free tier)       |

## License

MIT License - see [LICENSE](LICENSE) for details.

## Author

**Srinivas Pogiri**  
AWS Cloud Engineer | Hyderabad, India  
[GitHub](https://github.com/pogiri-srinivas)
