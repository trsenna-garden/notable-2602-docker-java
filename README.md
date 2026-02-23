# Docker & Java + Spring Boot

Este projeto serve como um modelo de referência (boilerplate) para a containerização de aplicações Java utilizando Spring Boot, Maven e as melhores práticas de Docker.

O objetivo principal é demonstrar um fluxo de build eficiente, resultando em imagens leves, seguras e otimizadas.

## 🚀 Tecnologias
- **Java 17** (Eclipse Temurin)
- **Spring Boot 4.x**
- **Maven**
- **Docker** (Multi-stage Build)

## 🛠️ Destaques do Projeto

### Dockerfile Otimizado
O `Dockerfile` incluído neste projeto utiliza a estratégia de **Multi-stage Build**:
1.  **Stage 1 (Builder):** Utiliza uma imagem completa do Maven para compilar o código e baixar dependências.
    -   Usa `mvn dependency:go-offline` para cachear dependências, acelerando builds subsequentes.
2.  **Stage 2 (Runtime):** Utiliza apenas o JRE (Java Runtime Environment), tornando a imagem final significativamente menor e mais segura (reduzindo a superfície de ataque).

### Build Previsível
Configuramos o `pom.xml` com a tag `<finalName>app</finalName>` para garantir que o artefato gerado tenha sempre o mesmo nome, facilitando a automação e evitando erros de cópia no Docker.

## 📦 Como Executar

### Pré-requisitos
- Docker instalado.

### Passo a Passo

1.  **Construir a imagem Docker:**
    ```bash
    docker build -t trsenna/notable-2602-docker-java .
    ```

2.  **Executar o container:**
    ```bash
    docker run --rm -p 9000:8080 trsenna/notable-2602-docker-java
    ```
    A aplicação estará disponível em `http://localhost:8080`.

## 📂 Estrutura de Arquivos
- `Dockerfile`: Configuração da imagem.
- `pom.xml`: Gerenciamento de dependências e build do Maven.
- `src/`: Código fonte da aplicação Spring Boot.

---
*Este projeto foi criado para fins de estudo e como modelo para futuros desenvolvimentos em Java/Docker.*
