# Portal Cativo – Gás Verde (Wi-Fi Visitantes)

Página no mesmo estilo do portal da Urca (tela de boas-vindas → formulário → acesso liberado), com logo e cores da Gás Verde.

## Arquivos
- `index.html` – portal completo (HTML + CSS + JS em um arquivo, sem dependências externas)
- `images/logo-gasverde-branca.png` – logo branco (tela inicial)
- `images/logo-gasverde.png` – logo colorido com fundo transparente (formulário)
- `images/favicon.svg` – ícone da marca
- `videos/fundo.mp4` – vídeo institucional do Grupo Urca (o mesmo do portal da Urca), **sem áudio**, sem as legendas, 960px, 5,5 MB (o original tinha 61 MB). Para trocar, basta substituir o arquivo mantendo o nome.

## Cores usadas (tiradas do logo)
| Uso | Cor |
|---|---|
| Verde principal | `#017562` |
| Fundo | `#01493d` → `#012e27` |
| Destaque (verde claro) | `#82ed70` |

## Diferenças em relação ao portal da Urca
- **Libera de verdade no Meraki**: usa `base_grant_url` + `user_continue_url` (o da Urca só simula o envio).
- **Vídeo de fundo leve e mudo**: o visitante ainda não tem internet ao abrir o portal, então o vídeo precisa ser pequeno (o da Urca tem 61 MB).
- **Cartões semitransparentes** (efeito vidro) para o vídeo aparecer por trás.
- **Sem fontes/CDN externos**: não precisa liberar domínios extras no Walled Garden.
- **Aceite de Termos/LGPD obrigatório** + validação de nome, e-mail, telefone (com máscara) e empresa.
- **Gravação dos dados opcional**: preencha `ENDPOINT_CADASTRO` no início do script (Google Apps Script, Power Automate etc.). Vazio = só libera, sem gravar.

## Como publicar (GitHub Pages)
1. No repositório `acessogv/formulario-gasverde` (ou um novo), substitua `index.html` e envie a pasta `images/`.
2. O antigo `aguarde.html` não é mais necessário.
3. Settings → Pages → branch `main` → `/root`.

## Configuração no Meraki (rede Gas Verde - Seropédica)
- Wireless → Access control → **GV_Visitantes** → Splash page: **Click-through** (já está).
- Wireless → Splash page → **Custom splash URL**: `https://acessogv.github.io/formulario-gasverde/` (mesmo endereço de hoje, se publicar no mesmo repositório).
- Access control → Advanced splash settings → **Walled garden**: liberar `acessogv.github.io` (e o domínio do `ENDPOINT_CADASTRO`, se usar).

## Testar fora do Wi-Fi
Abra o `index.html` no navegador: o fluxo funciona em "modo de teste" e, no fim, abre gasverde.com.br em vez de liberar a rede.
