# Plataforma Mobile de Apoio à Memorização e Revisão

## Sobre o Projeto
Este projeto consiste em uma plataforma mobile voltada para estudantes, com foco em **memorização** e **revisão ativa**

<p align="center">
  <img src="https://github.com/user-attachments/assets/6a53b89d-6007-4833-9118-ade2e4388a7e" width="100%"/>
</p>

### Funcionalidades

A plataforma contará com diversos formatos de exercícios e interações:

### Entrada de Resposta
- **Pergunta Digitada**  
  O usuário digita a resposta correta.

---

### Múltipla Escolha
- **Múltipla Escolha**  
  Seleção da alternativa correta entre opções.

---

### Flashcards
- **Flashcard Manual (Frente e Verso)**  
  Criação de cartões para revisão rápida.
- Ideal para memorização de conceitos e definições.

---

### Exercícios Interativos
- **Complete o Texto**  
  Preenchimento de lacunas em textos.
  
- **Ordenação**  
  Organização de itens na sequência correta.

- **Seleção de Itens**  
  Escolha dos elementos corretos dentro de um conjunto.

---

### Associação e Classificação
- **Itens por Fases**  
  Associação de elementos a etapas de um processo.

- **Itens por Categoria**  
  Classificação de itens em categorias específicas.

- **Arrastar por Categoria**  
  Classificação via drag-and-drop.

- **Arrastar por Fases**  
  Organização de itens conforme etapas.

---

### Recursos Visuais
- **Oclusão de Imagem**  
  Ocultação de partes de uma imagem para treino visual.

- **Linha do Tempo**  
  Organização cronológica de eventos ou fases.

---

### Estruturas em Quadro
- **Preencher Quadro**  
  Relacionar processos e áreas.

- **Quadro - Escolha por Linha**  
  Selecionar opções dentro de linhas.

- **Quadro - Escolha por Célula**  
  Interação baseada em células específicas.

---

## Possíveis Expansões
- Sistema de repetição espaçada (SRS)
- Gamificação (pontuação, níveis, conquistas)
- Análise de desempenho do usuário
- Recomendações personalizadas de estudo
- Integração com IA para geração de conteúdo

## Organização de Arquivos e Telas

```text
MemoBrain/
├── app/
│   └── src/main/java/com/memobrain/memonow/
│
│       ├── MainActivity.kt
│       │   └── Ponto de entrada do aplicativo. Configura o tema e inicia a navegação.
│
│       ├── navegacao/
│       │   ├── AppNavegacao.kt
│       │   │   └── Controla o fluxo entre as telas do aplicativo.
│       │   └── rotas_telas.kt
│       │       └── Define as rotas usadas pela navegação.
│
│       ├── data/
│       │   ├── local/
│       │   │   └── datastore/
│       │   │       ├── ArmazenamentoSessao.kt
│       │   │       │   └── Salva localmente UID e e-mail da sessão atual.
│       │   │       └── PreferenciasUsuario.kt
│       │   │           └── Reservado para preferências do usuário, como tema e notificações.
│       │   │
│       │   ├── remote/
│       │   │   ├── autenticacao/
│       │   │   │   ├── GerenciadorAutenticacao.kt
│       │   │   │   │   └── Centraliza funções gerais de autenticação.
│       │   │   │   ├── ServicoCadastroFirebase.kt
│       │   │   │   │   └── Cria usuários no Firebase Authentication e salva o perfil no Firestore.
│       │   │   │   └── ServicoLoginFirebase.kt
│       │   │   │       └── Realiza login, logout e consulta o usuário autenticado.
│       │   │   │
│       │   │   └── firestore/
│       │   │       ├── FonteDadosFirestoreCaderno.kt
│       │   │       │   └── Comunicação direta com a coleção de cadernos.
│       │   │       ├── FonteDadosFirestoreArquivo.kt
│       │   │       │   └── Comunicação direta com os arquivos de cada caderno.
│       │   │       ├── FonteDadosFirestoreConteudo.kt
│       │   │       │   └── Gerencia flashcards e questões de múltipla escolha.
│       │   │       └── FonteDadosFirestoreHistorico.kt
│       │   │           └── Salva e consulta o histórico de revisões.
│       │   │
│       │   └── repository/
│       │       └── repositorio/
│       │           ├── RepositorioCaderno.kt
│       │           ├── RepositorioArquivo.kt
│       │           ├── RepositorioConteudo.kt
│       │           └── RepositorioHistorico.kt
│       │
│       │           └── Faz a ponte entre as telas/ViewModels e o Firestore.
│
│       ├── features/
│       │   ├── login/
│       │   │   ├── TelaInicial.kt
│       │   │   │   └── Tela de boas-vindas com opções de entrar ou cadastrar.
│       │   │   └── LoginTela.kt
│       │   │       └── Tela usada para autenticação de usuários cadastrados.
│       │   │
│       │   ├── registrar/
│       │   │   └── RegistrarTela.kt
│       │   │       └── Tela de criação de uma nova conta.
│       │   │
│       │   ├── perfil/
│       │   │   └── ConfigTela.kt
│       │   │       └── Exibe dados do perfil, plano atual e opções de sair ou excluir conta.
│       │   │
│       │   └── cadernos/
│       │       ├── DashboardCadernosTela.kt
│       │       │   └── Tela inicial do app: métodos de estudo, cadernos em andamento e atividades recentes.
│       │       │
│       │       ├── HomeViewModel.kt
│       │       │   └── Controla os dados exibidos na tela inicial.
│       │       │
│       │       ├── ListaCadernosTela.kt
│       │       │   └── Lista todos os cadernos do usuário autenticado.
│       │       │
│       │       ├── CadernosViewModel.kt
│       │       │   └── Controla o carregamento e atualização da lista de cadernos.
│       │       │
│       │       ├── CriarCadernoScreen.kt
│       │       ├── CriarCadernoViewModel.kt
│       │       │   └── Criam novos cadernos.
│       │       │
│       │       ├── EditNotebookScreen.kt
│       │       ├── EditNotebookViewModel.kt
│       │       │   └── Editam ou excluem um caderno existente.
│       │       │
│       │       ├── DetalheCadernoScreen.kt
│       │       ├── DetalheCadernoViewModel.kt
│       │       │   └── Exibem os arquivos pertencentes a um caderno.
│       │       │
│       │       ├── CriarArquivoScreen.kt
│       │       ├── CriarArquivoViewModel.kt
│       │       │   └── Criam arquivos de estudo dentro de um caderno.
│       │       │
│       │       ├── EditArquivoScreen.kt
│       │       ├── EditArquivoViewModel.kt
│       │       │   └── Editam ou excluem arquivos já criados.
│       │       │
│       │       ├── CreateFlashcardScreen.kt
│       │       ├── CreateFlashcardViewModel.kt
│       │       │   └── Criam perguntas abertas no formato de flashcard.
│       │       │
│       │       ├── CreateMultipleChoiceScreen.kt
│       │       ├── CreateMultipleChoiceViewModel.kt
│       │       │   └── Criam questões de múltipla escolha.
│       │       │
│       │       ├── RevisarArquivoScreen.kt
│       │       ├── RevisarArquivoViewModel.kt
│       │       │   └── Controlam a revisão de perguntas e registram o progresso.
│       │       │
│       │       ├── FlashcardSummaryScreen.kt
│       │       ├── FlashcardSummaryViewModel.kt
│       │       │   └── Exibem o resultado da revisão, com acertos e tempo.
│       │       │
│       │       └── GraficosTelas.kt
│       │           └── Exibe gráficos de desempenho e evolução do usuário.
│       │
│       └── ui/
│           ├── componentes/
│           │   ├── Botao.kt
│           │   └── SocialLoginBotao.kt
│           │
│           │   └── Componentes reutilizáveis usados em diferentes telas.
│           │
│           └── tema/
│               ├── Color.kt
│               ├── Theme.kt
│               └── Type.kt
│
│               └── Define cores, tipografia e tema visual do aplicativo.
```
