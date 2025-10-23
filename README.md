# QR Code Generator with AWS S3 Integration

[![Spring Boot](https://img.shields.io/badge/Spring_Boot-3.5.3-green.svg)]()
[![Java](https://img.shields.io/badge/Java-21-blue.svg)]()
[![Docker](https://img.shields.io/badge/Docker-✓-blue.svg)]()

Aplicação Spring Boot para gerar QR Codes e armazená-los automaticamente no AWS S3.

## 📋 Funcionalidades
- Geração de QR Codes a partir de URLs/texto
- Upload automático para bucket AWS S3
- Configuração dinâmica de tamanho/cor do QR Code
- Endpoint REST para geração sob demanda
- Pronta para execução em containers Docker

## ⚙️ Tecnologias
- **Java 21**
- **Spring Boot 3.5.3**
- **Google ZXing** (Geração de QR Codes)
- **AWS SDK for Java 2.x** (Integração com S3)
- **Docker** (Empacotamento e deploy)

## 🚀 Como Executar

### Pré-requisitos
- Java 21 JDK
- Maven 3.9+
- Conta AWS com acesso ao S3
- Docker (opcional)

### Configuração
Crie um arquivo `.env` na raiz do projeto com:
AWS_ACCESS_KEY_ID=SUA_ACCESS_KEY
AWS_SECRET_ACCESS_KEY=SUA_SECRET_KEY

```no application.properties
spring.application.name=qrcode.generator
AWS_REGION=us-east-1
S3_BUCKET_NAME=meu-bucket-qrcodes

Execução Local
mvn spring-boot:run

Build e Execução com Docker

docker build --build-arg AWS_ACCESS_KEY_ID=<sua-key> \
             --build-arg AWS_SECRET_ACCESS_KEY=<sua-secret> \
             -t qrcode-generator .

docker run -p 8080:8080 qrcode-generator

Estrutura do Projeto

src/
├── main/
│   ├── java/
│   │   └── com/viniciusbonilha/qrcode/generator/
│   │       ├── Application.java               # Classe principal
│   │       ├── controller/
│   │       │   └── QrCodeController.java      # Controlador REST
│   │       ├── dto/
│   │       │   ├── QrCodeGenerateRequest.java # DTO de requisição
│   │       │   └── QrCodeGenerateResponse.java# DTO de resposta
│   │       ├── infrastructure/
│   │       │   └── S3StorageAdapter.java      # Implementação do S3
│   │       ├── ports/
│   │       │   └── StoragePort.java           # Porta de armazenamento
│   │       └── service/
│   │           └── QrCodeGeneratorService.java# Serviço de geração
│   └── resources/
│       └── application.properties             # Configurações
├── test/
└── Dockerfile                                # Configuração Docker
