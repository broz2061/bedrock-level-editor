# Bedrock World Suite

Ferramenta web para visualizar e editar mundos do **Minecraft Bedrock Edition**, direto no navegador. Não precisa instalar nada, e os seus arquivos não são enviados para nenhum servidor.

**Acesse:** https://SEU_USUARIO.github.io/NOME_DO_REPOSITORIO/

> **Faça backup do seu mundo antes de usar.** Teste sempre as alterações numa **cópia**.

## O que ela faz

### 1. Editor de `level.dat`
- Lê o NBT Little-Endian do Bedrock (com o cabeçalho de 8 bytes) e mostra como JSON.
- Preserva os tipos (`byte`, `short`, `int`, `long`, `float`, `double`, `string`) e os números de 64 bits sem perda de precisão.
- Painel guiado com interruptores e opções clicáveis (modo de jogo, dificuldade, algumas gamerules) sincronizado com o JSON.
- Funciona também com o `level.dat_old`.

### 2. Inspetor de LevelDB (`db/`)
- Lê os arquivos `.log` do banco do mundo (`CURRENT`, `MANIFEST-xxxxxx` e `.log`).
- Mostra os jogadores (`~local_player` e `player_server_...`): posição, dimensão, nível de XP, armadura, mão secundária, inventário e baú do Fim.
- Lista os baús, barris, shulker boxes, funis, dispensers e similares que têm itens, com as coordenadas.
- **Editor de inventário:** clique em um slot para trocar o item, a quantidade, o nome personalizado, os encantamentos, o `CanPlaceOn` e o `CanDestroy`, ou para esvaziar o slot. A alteração é gravada como um novo registro no final do `.log` e vai no `.zip` do mundo.

### 3. Visualizador de `.mcstructure`
- Lê estruturas salvas pelo jogo (NBT sem cabeçalho), mostra a paleta de blocos e um visualizador por camadas de altura (Y).

### Pasta do mundo e `.zip`
- Abre a pasta do mundo inteira (Chrome ou Edge) e exporta o mundo modificado em `.zip`.

## Como usar

1. Abra o site.
2. Escolha o `level.dat` ou a pasta do mundo.
3. Edite pelo painel guiado ou pelo JSON.
4. Baixe o arquivo ou o `.zip` do mundo e coloque na pasta do jogo (com o jogo **fechado**).

### Onde ficam os mundos

- **Windows (Bedrock atual):** `%AppData%\Minecraft Bedrock\Users\<ID do jogador>\games\com.mojang\minecraftWorlds\<pasta do mundo>`
- **Windows (versão antiga, UWP):** `%LocalAppData%\Packages\Microsoft.MinecraftUWP_8wekyb3d8bbwe\LocalState\games\com.mojang\minecraftWorlds\`
- **Android:** `Android/data/com.mojang.minecraftpe/files/games/com.mojang/minecraftWorlds/`

## Limitações conhecidas

- **Arquivos `.ldb` não são lidos.** Só os `.log` são. Em mundos antigos ou grandes, parte dos dados fica em `.ldb` e não aparece. Nesses mundos a edição de inventário fica **desativada**.
- **A edição de inventário não foi confirmada dentro do jogo.** A gravação foi verificada nos arquivos (CRC válido, original preservado), mas não abri um mundo editado no Minecraft. Teste numa cópia.
- O local exato de `CanPlaceOn` e `CanDestroy` no item (`tag.CanPlaceOn` / `tag.CanDestroy`) segue o formato antigo e pode não valer para versões mais novas.
- A lista de IDs de encantamento (0 a 37) foi escrita de memória.
- Ao trocar um item por outro bloco, os estados do bloco voltam ao padrão.
- **Importar estruturas no mundo ainda não existe.** O botão está desativado.
- Não há visualização 3D, apenas por camadas.
- O mundo é carregado inteiro na memória do navegador, então mundos muito grandes podem ficar pesados.
- O Minecraft Java **não** é suportado (usa outro formato).

## Privacidade

Todo o processamento acontece no seu navegador. Os seus arquivos não são enviados para a internet. O único recurso externo é a biblioteca **JSZip**, carregada de uma CDN para gerar o `.zip`.

## Publicar no GitHub Pages

1. Coloque o `index.html` e este `README.md` na **raiz** do repositório (**Add file > Upload files**).
2. Em **Settings > Pages**, escolha **Deploy from a branch**, branch `main`, pasta `/ (root)`, e clique em **Save**.
3. Em 1 a 2 minutos o site fica em `https://broz2061.github.io/bedrock-level-editor/`. Para ver uma atualização, use **Ctrl+F5**.

O repositório precisa ser **público** para o Pages gratuito funcionar.

## Aviso

Projeto não oficial, sem relação com a Mojang Studios nem com a Microsoft. Minecraft é marca registrada da Mojang AB. Use por sua conta e risco.

## Licença

Defina a licença do projeto (por exemplo, MIT) adicionando um arquivo `LICENSE`.
