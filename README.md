# transcritor-audio-whisper
Aplicativo desktop para transcrição de áudio usando Faster Whisper, com interface gráfica em Tkinter.

# Transcritor de Áudio 'CesarVox' com Faster Whisper

Este é um aplicativo desktop simples, construído com Python e Tkinter, para transcrever arquivos de áudio em texto utilizando a biblioteca [Faster Whisper](https://github.com/guillaumekln/faster-whisper). Ele oferece uma interface gráfica amigável para selecionar o arquivo de áudio, escolher o modelo de transcrição (tamanho do modelo Whisper), optar por usar GPU (se disponível) e salvar o resultado em um arquivo de texto.

## Funcionalidades

* **Seleção de Arquivo de Áudio:** Interface intuitiva para localizar e selecionar o arquivo de áudio.
* **Sugestão Inteligente de Saída:** O nome do arquivo de saída é automaticamente sugerido com base no nome do arquivo de áudio original (ex: `Transcricao-NomeDoSeuAudio.txt`).
* **Seleção de Modelo Whisper:** Escolha entre diferentes tamanhos de modelo (tiny, base, small, medium, large) para equilibrar velocidade e precisão.
* **Suporte a GPU:** Opção para utilizar a GPU (NVIDIA CUDA) para uma transcrição mais rápida, se uma GPU compatível e os drivers/bibliotecas corretas (PyTorch com CUDA) estiverem instalados. Caso contrário, a transcrição será executada na CPU.
* **Barra de Progresso:** Acompanhe o progresso da transcrição em tempo real.
* **Botão de Cancelamento:** Permite parar uma transcrição em andamento.
* **Instalação Automática de Dependências:** O script tenta instalar `faster-whisper` e `torch` automaticamente se não forem encontrados.

## Requisitos

* Python 3.8+ (testado com Python 3.12)
* `faster-whisper`
* `torch` (para uso da GPU, caso contrário, a CPU será utilizada)

## Como Usar

### 1. Baixe o Script

1.  Clone este repositório ou baixe o arquivo `transcritor_whisper.py` para o seu computador.

### 2. Execute o Script

1.  Abra um terminal (prompt de comando no Windows, Terminal no macOS/Linux) na pasta onde você salvou o script.
2.  Execute o script com o seguinte comando:
    ```bash
    python transcritor_whisper.py
    ```
3.  **Instalação Automática:** Na primeira execução, o script tentará instalar `faster-whisper` e `torch` (se ainda não estiverem instalados) usando `pip`. Certifique-se de ter conexão com a internet. Se houver problemas, tente instalar manualmente (veja "Instalação Manual de Dependências" abaixo).

### 3. Usando a Interface Gráfica

1.  **Usar GPU (se disponível):** Marque esta opção se você tiver uma GPU NVIDIA com CUDA configurado e quiser acelerar a transcrição. Se não tiver, desmarque (ou o script usará a CPU automaticamente com um aviso).
2.  **Modelo Whisper:** Escolha o tamanho do modelo. Modelos maiores (`medium`, `large`) são mais precisos, mas exigem mais memória e tempo de processamento. Modelos menores (`tiny`, `base`, `small`) são mais rápidos.
3.  **Arquivo de Áudio:** Clique em **"Procurar"** para selecionar o arquivo de áudio que deseja transcrever. Formatos suportados incluem `.mp3`, `.wav`, `.m4a`, `.flac`.
4.  **Salvar Transcrição Como:** Este campo será preenchido automaticamente com uma sugestão de nome (`Transcricao-NomeDoSeuAudio.txt`). Você pode clicar em **"Salvar"** para escolher outro local e nome para o arquivo de texto da transcrição.
5.  **Transcrever:** Clique neste botão para iniciar o processo de transcrição. A barra de progresso e a mensagem de status serão atualizadas.
6.  **Parar/Cancelar:** Clique neste botão para interromper a transcrição em andamento.

## Solução de Problemas

* **"Aviso: CUDA não está disponível..."**: Isso significa que o PyTorch não conseguiu detectar uma GPU compatível com CUDA. A transcrição continuará na CPU. Se você tem uma GPU NVIDIA, verifique a instalação dos drivers e do PyTorch com suporte a CUDA.
* **Erro na instalação de pacotes**: Se a instalação automática falhar, pode ser devido a problemas de permissão ou conexão. Tente instalar manualmente os pacotes.

### Instalação Manual de Dependências (se a automática falhar)

Abra seu terminal e execute os seguintes comandos:

```bash
pip install faster-whisper --user
pip install torch --user  # Para transcrição em CPU
# OU
# pip install torch torchvision torchaudio --index-url [https://download.pytorch.org/whl/cu118](https://download.pytorch.org/whl/cu118) --user # Exemplo para CUDA 11.8. Adapte para sua versão CUDA.
