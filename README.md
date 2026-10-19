# Game Editor — MCP

Crie jogos 2D/2.5D conversando com um agente de IA (Claude Code, Claude Desktop ou outro cliente MCP). O agente usa as mesmas operações que uma pessoa faz no editor visual — criar cenas e camadas, colocar objetos, ajustar componentes, montar eventos, conversas e textos, importar imagens e sons — e pode **jogar o jogo** para conferir (fotos da tela e estado do jogo) e **exportar** para Windows ou Web.

Este pacote traz só os programas já compilados; o código-fonte não faz parte dele.

## O que vem no zip

| Pasta / arquivo | Para quê |
| --- | --- |
| `game_mcp.exe` | O servidor MCP (o agente conversa com ele). |
| `player/` | O jogador do Windows: usado pelo `play_test` e pela exportação para Windows. |
| `player_web/` | O jogador Web: usado pela exportação para Web. |
| `player_android/` | O jogador Android (APK): usado pela exportação para Android. |
| `exemplos/` | Projetos de exemplo (`.gameproj`): plataforma, nave, corrida, cartas, romance, apocalipse zumbi... |

## Requisitos

- Windows 10 ou 11 (64 bits).
- Um cliente MCP. Os exemplos abaixo usam o [Claude Code](https://claude.com/claude-code).

## Instalação

1. Baixe o `game-editor-mcp-<versão>.zip` da página **Releases** deste repositório.
2. Descompacte numa pasta fixa, por exemplo `C:\game-editor-mcp` (mantenha `player`, `player_web`, `player_android` e `exemplos` ao lado do `game_mcp.exe`).
3. Cadastre o servidor no seu cliente:

**Claude Code** (no terminal):

```bash
claude mcp add game-editor --scope user -- C:\game-editor-mcp\game_mcp.exe
```

**Claude Desktop** (`claude_desktop_config.json`):

```json
{
  "mcpServers": {
    "game-editor": { "command": "C:\\game-editor-mcp\\game_mcp.exe" }
  }
}
```

4. Abra uma conversa nova e peça, por exemplo:

> Abra o exemplo "pulo", jogue um pouco e me mostre como está. Depois crie uma fase nova com três plataformas e uma moeda no alto.

## Como usar

- **Comece por um exemplo** (`examples` lista os que vêm no kit) ou por um projeto novo (`new_project`).
- O agente **salva** com `save_project` (arquivo `.gameproj`); esse arquivo também abre no editor visual.
- **`play_test`** abre a janela do jogo por alguns segundos, segue um roteiro de teclas e devolve fotos e o estado do jogo. É normal a janela aparecer e fechar sozinha.
- **`export_game`** gera o jogo pronto para Windows, Web ou Android, com os jogadores do kit. O jogo Web precisa ser servido por um servidor HTTP (não abre com duplo clique). O Android sai num `.apk` (Android 7 ou mais novo) assinado com a chave do jogo, criada na primeira exportação em `<pasta de saída>/<id do app>.chave.json`: **guarde uma cópia** — sem ela, uma versão nova do jogo não instala por cima da antiga.
- Imagens e sons próprios entram com `import_asset` (PNG, JPG, WebP, WAV, MP3, OGG e folhas de sprites).

## Atualizar

Baixe o zip da versão nova e substitua a pasta inteira. Os seus projetos `.gameproj` ficam onde você os salvou e continuam abrindo.

## Problemas comuns

- **"player não encontrado"**: a pasta `player` não está ao lado do `game_mcp.exe`.
- **O Windows bloqueou o programa** (SmartScreen): clique em "Mais informações" → "Executar assim mesmo", ou clique com o botão direito no zip antes de descompactar → Propriedades → "Desbloquear".
- **O agente não vê as ferramentas**: confira o caminho no cadastro do servidor e reinicie o cliente.

## Licença

Uso livre para criar e publicar os seus jogos. Os programas são fornecidos como estão, sem garantia. Não é permitido descompilar, redistribuir modificado ou vender o kit em si. Todos os direitos reservados.
