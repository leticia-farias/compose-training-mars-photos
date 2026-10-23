# Mars Photos App (Jetpack Compose)

Este repositório contém a implementação prática desenvolvida durante a trilha de [**Rede e Consumo de API em Jetpack Compose**](https://developer.android.com/codelabs/basic-android-kotlin-compose-getting-data-internet?hl=pt-br#0) do Android Basics Codelab, disponibilizado pelo Google.

O objetivo desta aplicação é demonstrar o consumo de serviços web RESTful de forma assíncrona, desserialização de JSON em objetos de domínio Kotlin e renderização dinâmica de imagens capturadas pelos rovers de Marte em uma grade interativa no Compose.

## Tecnologias e Ferramentas Utilizadas

- **Linguagem:** Kotlin
- **UI Framework:** Jetpack Compose (Material Design 3)
- **Conectividade & Rede:** Retrofit 2 & OkHttp
- **Conversão de Dados:** `kotlinx.serialization` (JSON converter)
- **Carregamento de Imagens Assíncrono:** Coil para Jetpack Compose (`AsyncImage`)
- **Arquitetura:** MVVM (Model-View-ViewModel) com `StateFlow` / UI State
- **Coroutines & Asynchrony:** Kotlin Coroutines para chamadas de rede não bloqueantes
- **IDE:** Android Studio
- **Mínimo SDK:** API level 21+

## Conceitos e Aprendizados Práticos

Durante o desenvolvimento deste projeto, os seguintes conceitos foram consolidados:

### 1. Comunicação HTTP com Retrofit
- Configuração de cliente Retrofit com base URL e conversores de tipo (`kotlinx.serialization.converter`).
- Declaração de rotas da API em interfaces Kotlin anotadas com `@GET` e funções suspendíveis (`suspend functions`).

### 2. Gerenciamento do Estado da UI de Rede (Sealed Interfaces)
- Estruturação do estado da tela através de uma sealed interface (`MarsUiState`):
  - **`Success`**: Dados carregados com sucesso.
  - **`Error`**: Falhas de conexão, erro 4xx/5xx ou parsing incorreto.
  - **`Loading`**: Exibição de indicador de progresso (*placeholders* e animações de carregamento).

### 3. Exibição de Imagens Remotas com Coil
- Uso do composable `AsyncImage` para efetuar requisições de mídia assíncronas.
- Tratamento de estados visuais com ícones de carregamento (`loading_img`) e erro de conexão (`ic_broken_image`).

### 4. Layouts Dinâmicos e Reativos
- Renderização do catálogo de imagens em uma grade responsiva com `LazyVerticalGrid`.
- Integração de `ViewModel` gerenciando e expondo a lista de fotos de Marte de forma reativa.

## Evidências do Projeto (Demonstração Prática)

### 1. Estados da Interface de Usuário

| Estado de Sucesso | Estado de Carregamento | Estado de Erro de Conexão |
| :---: | :---: | :---: |
| <img src="screenshots/mars_success.png" width="30%" alt="Mars Photos Success State"> | <img src="screenshots/mars_loading.png" width="30%" alt="Mars Photos Loading State"> | <img src="screenshots/mars_error.png" width="30%" alt="Mars Photos Error State"> |

## Como Executar o Projeto

1. Clone o repositório:
   ```bash
   git clone https://github.com/leticia-farias/compose-training-mars-photos.git
2. Abra o projeto no Android Studio.
3. Aguarde o término da sincronização do Gradle.
4. Garanta que o dispositivo/emulador possua acesso à internet.
5. Execute o aplicativo em um emulador ou dispositivo físico (API 21+).
