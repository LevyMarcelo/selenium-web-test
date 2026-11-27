# Automação de Testes Web com Selenium e Java

## 1. Visão geral do projeto

Projeto de automação de testes Web com Selenium e Java, aplicando práticas de organização e reutilização de componentes, além de validação funcional em diferentes navegadores.

## 2. Objetivos

Desenvolver uma solução de automação de testes Web, priorizando:

- Automação de fluxos funcionais.
- Validação dos comportamentos da aplicação.
- Reutilização e manutenibilidade dos componentes.
- Execução dos testes em diferentes navegadores.

## 3. Aplicação sob teste

**Google Brasil**

Aplicação utilizada para validar o fluxo de pesquisa e a apresentação dos resultados.

## 4. Tecnologias utilizadas

- **Selenium 4.5.0:** framework de automação de testes Web.
- **Java 11:** linguagem utilizada no desenvolvimento dos testes.
- **TestNG 7.6.1:** framework para organização e execução dos testes.
- **Hamcrest 1.3:** biblioteca utilizada nas verificações e assertions.
- **Gradle:** ferramenta de gerenciamento de dependências e build.
- **WebDriverManager 5.3.0:** gerenciamento dos drivers dos navegadores.

## 5. Estratégia de testes

A estratégia contempla a automação de um fluxo de pesquisa no Google Brasil, com foco na interação com os elementos da interface e na validação do resultado apresentado.

Na implementação, são adotadas práticas que favorecem a organização e a manutenibilidade:

- Utilização de Page Object Model.
- Separação entre configuração do ambiente e implementação dos testes.
- Utilização de esperas explícitas para sincronização com a interface.
- Validação dos resultados utilizando Hamcrest.

## 6. Escopo de testes

O escopo automatizado contempla o fluxo de pesquisa no Google Brasil.

| Etapa | Validação |
|---|---|
| Acesso à aplicação | Abertura do Google Brasil |
| Pesquisa | Preenchimento do campo de busca com o termo `Selenium` |
| Acionamento da pesquisa | Execução da pesquisa |
| Resultado | Recuperação do texto do primeiro resultado |
| Assertion | Verificação do resultado esperado: `Downloads - Selenium.dev` |

A validação compara o texto apresentado no primeiro resultado com o conteúdo esperado.

## 7. Arquitetura do projeto

A automação utiliza o padrão **Page Object Model (POM)** para separar os elementos e as interações da interface da implementação dos testes.

A arquitetura está organizada em componentes com responsabilidades específicas:

- **Tests:** implementação dos cenários automatizados e respectivas validações.
- **Pages:** encapsulamento dos elementos e das interações com a página de pesquisa.
- **BaseTest:** estrutura compartilhada para inicialização e encerramento do WebDriver.
- **Utils:** métodos auxiliares para interação com elementos e sincronização.
- **TestNG XML:** configurações de execução por navegador e execução paralela.

## 8. Estrutura do projeto

```text
selenium-web-test/
│
├── src/
│   └── test/
│       ├── java/
│       │   └── br/com/selenium/
│       │       ├── pages/
│       │       │   └── SearchGooglePage.java
│       │       │
│       │       ├── tests/
│       │       │   ├── BaseTest.java
│       │       │   └── SearchGoogleTest.java
│       │       │
│       │       └── utils/
│       │           └── Utils.java
│       │
│       └── resources/
│           ├── chrome_test.xml
│           ├── firefox_test.xml
│           ├── safari_test.xml
│           ├── headless_test.xml
│           └── multi_browser_test.xml
│
├── .gitignore
├── build.gradle
├── settings.gradle
└── README.md
```

## 9. Pré-requisitos

A execução dos testes requer a configuração do ambiente de desenvolvimento e a disponibilidade dos navegadores utilizados.

**Ferramentas e dependências:**

- Java Development Kit (JDK) 11.
- Gradle.
- Git.
- Google Chrome para execução no Chrome.
- Mozilla Firefox para execução no Firefox.
- macOS e Safari habilitado para execução no Safari.

O WebDriverManager é utilizado para auxiliar no gerenciamento dos drivers dos navegadores.

## 10. Instalação e configuração

**Clonar o repositório:**

```bash
git clone <URL_DO_REPOSITORIO>
```

**Acessar o diretório:**

```bash
cd selenium-web-test
```

**Preparar o projeto:**

Importar o projeto na IDE e aguardar a resolução das dependências do Gradle.

## 11. Execução dos testes

O projeto utiliza arquivos XML do TestNG para configurar a execução dos testes por navegador.

As configurações estão disponíveis em `src/test/resources/`:

| Suíte | Configuração |
|---|---|
| `chrome_test.xml` | Execução no Google Chrome |
| `firefox_test.xml` | Execução no Mozilla Firefox |
| `safari_test.xml` | Execução no Safari |
| `headless_test.xml` | Execução do Chrome em modo headless |
| `multi_browser_test.xml` | Execução paralela em diferentes navegadores |

**Execução pelo Gradle:**

```bash
# Google Chrome
gradle test -Psuite=chrome_test

# Mozilla Firefox
gradle test -Psuite=firefox_test

# Safari
gradle test -Psuite=safari_test

# Chrome Headless
gradle test -Psuite=headless_test

# Execução paralela em múltiplos navegadores
gradle test -Psuite=multi_browser_test
```

A suíte `multi_browser_test.xml` configura a execução paralela em quatro threads, contemplando Chrome, Safari, Firefox e Chrome Headless.

**Execução pela IDE IntelliJ IDEA:**

Também é possível executar as suítes diretamente pela IDE:

1. Abrir o projeto na IDE.
2. Acessar `src/test/resources/`.
3. Selecionar o arquivo XML desejado.
4. Executar a suíte utilizando o TestNG.

## 12. Resultados

O cenário automatizado realiza a pesquisa no Google Brasil e verifica o resultado apresentado por meio de uma assertion com Hamcrest.
