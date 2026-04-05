#  YouTube Downloader

Projeto Python para baixar vídeos e áudios do YouTube utilizando a biblioteca **pytubefix**. Suporta download de vídeo padrão, somente áudio e vídeo em HD (requer FFmpeg).

---

##  Funcionalidades

- **[1] Baixar vídeo** — Baixa o vídeo na maior resolução disponível via stream progressiva
- **[2] Baixar áudio** — Extrai somente o áudio do vídeo
- **[3] Baixar vídeo HD** — Baixa vídeo em alta definição (requer FFmpeg instalado)

---

##  Pré-requisitos

- Python 3.8 ou superior
- pip
- FFmpeg *(obrigatório apenas para a opção HD — veja instruções abaixo)*

---

##  Instalação do projeto

**1. Clone o repositório:**

```bash
git clone https://github.com/seu-usuario/seu-repositorio.git
cd seu-repositorio
```

**2. Instale as dependências Python:**

```bash
pip install -r requirements.txt
```

**3. Execute o programa:**

```bash
python main.py
```

---

##  Instalação do FFmpeg (obrigatório para vídeo HD)

O FFmpeg é necessário para mesclar streams de vídeo e áudio separadas, que é como o YouTube disponibiliza vídeos em alta definição (1080p, 1440p, 4K).

###  Windows

**Opção 1 — Via Winget (recomendado, Windows 10/11):**

```powershell
winget install --id=Gyan.FFmpeg -e
```

**Opção 2 — Manualmente:**

1. Acesse [https://ffmpeg.org/download.html](https://ffmpeg.org/download.html)
2. Em *Windows*, clique em **Windows builds from gyan.dev**
3. Baixe o arquivo `ffmpeg-release-essentials.zip`
4. Extraia o conteúdo para uma pasta, por exemplo: `C:\ffmpeg`
5. Adicione o FFmpeg ao PATH do sistema:
   - Abra **Painel de Controle → Sistema → Configurações avançadas do sistema → Variáveis de Ambiente**
   - Em *Variáveis do sistema*, selecione `Path` e clique em **Editar**
   - Clique em **Novo** e adicione: `C:\ffmpeg\bin`
   - Clique em **OK** em todas as janelas

6. Verifique a instalação abrindo o **Prompt de Comando** ou **PowerShell**:

```powershell
ffmpeg -version
```

---

###  macOS

**Via Homebrew (recomendado):**

```bash
brew install ffmpeg
```

Se não tiver o Homebrew instalado, instale primeiro:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Verifique a instalação:

```bash
ffmpeg -version
```

---

### 🐧 Linux (Ubuntu/Debian)

```bash
sudo apt update
sudo apt install ffmpeg
```

**Fedora / RHEL / CentOS:**

```bash
sudo dnf install ffmpeg
```

**Arch Linux:**

```bash
sudo pacman -S ffmpeg
```

Verifique a instalação:

```bash
ffmpeg -version
```

---

##  Verificando se o FFmpeg está configurado corretamente

Após a instalação, execute o seguinte comando no terminal:

```bash
ffmpeg -version
```

A saída esperada começa com algo como:

```
ffmpeg version 7.x.x Copyright (c) 2000-2024 the FFmpeg developers
```

Se o comando não for reconhecido no Windows, revise o passo de configuração do PATH e reinicie o terminal.

---

##  Estrutura do projeto

```
├── main.py           # Ponto de entrada — menu interativo
├── video.py          # Lógica de download de vídeo
├── audio.py          # Lógica de download de áudio
├── requirements.txt  # Dependências Python
├── Vídeos Baixados/  # Pasta criada automaticamente para vídeos
├── Áudios Baixados/  # Pasta criada automaticamente para áudios
└── README.md
```

---

##  Dependências principais

| Pacote | Versão | Descrição |
|--------|--------|-----------|
| pytubefix | 10.3.8 | Fork atualizado do pytube para download do YouTube |
| aiohttp | 3.13.3 | Cliente HTTP assíncrono |

Todas as dependências estão listadas em `requirements.txt`.

---

##  Observações

- Os vídeos e áudios são salvos nas pastas **`Vídeos Baixados`** e **`Áudios Baixados`**, criadas automaticamente no diretório onde o script for executado.
- A opção HD (opção 3) ainda está em desenvolvimento. Sem o FFmpeg instalado e configurado no PATH, o programa exibirá uma mensagem de aviso.
- Este projeto é destinado a uso pessoal. Respeite os Termos de Serviço do YouTube ao utilizá-lo.
