# Bedrock Level Editor

Editor de `level.dat` do Minecraft Bedrock que roda 100% no navegador.
Seu arquivo nunca sai do seu computador.

**Acesse:** https://darozbruninho2-spec.github.io/bedrock-level-editor/

## O que faz
- Decodifica o `level.dat` (NBT Little-Endian com cabeçalho de 8 bytes) para JSON
- Editor guiado: modo de jogo, dificuldade, gamerules, seed, spawn e mais
- Edição completa pelo JSON, preservando os tipos (byte, int, long, float...)
- Gera o `level.dat` de volta e, se quiser, também o `level.dat_old`

## Como usar
1. Abra o site e clique em "Abrir o editor"
2. Escolha o `level.dat` do seu mundo e clique em "Decodificar"
3. Edite pelo painel guiado ou pelo JSON
4. Clique em "Salvar e baixar" e coloque o arquivo na pasta do mundo

**Faça backup do `level.dat` original antes de substituir.**

## Aviso
Projeto não oficial, sem afiliação com a Mojang ou a Microsoft.
Use por sua conta e risco.
