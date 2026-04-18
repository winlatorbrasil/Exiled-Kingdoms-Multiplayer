<![CDATA[<div align="center">

# ⚔️ Exiled Kingdoms — Sorrow Mod

### *Uma experiência multiplayer reimaginada*

[![Platform](https://img.shields.io/badge/Platform-Android-brightgreen?style=for-the-badge&logo=android)](https://developer.android.com)
[![Engine](https://img.shields.io/badge/Engine-LibGDX-red?style=for-the-badge)](https://libgdx.com)
[![Mode](https://img.shields.io/badge/Mode-LAN%20Co--op%20%2B%20PVP-blue?style=for-the-badge)](/)
[![Languages](https://img.shields.io/badge/Languages-7-orange?style=for-the-badge)](/)

---

*Mod completo para Exiled Kingdoms com multiplayer LAN aprimorado, arena PVP,*  
*NPCs e questlines exclusivos, UI medieval redesenhada e muito mais.*

</div>

---

## 📋 Sumário

- [🎮 Multiplayer LAN](#-multiplayer-lan)
- [⚔️ Arena PVP](#️-arena-pvp)
- [🧙 NPCs & Questlines Exclusivos](#-npcs--questlines-exclusivos)
- [🎨 Interface Medieval](#-interface-medieval)
- [📦 Sistema de Loot Aprimorado](#-sistema-de-loot-aprimorado)
- [🌍 Idiomas Suportados](#-idiomas-suportados)
- [🔧 Correções Técnicas](#-correções-técnicas)
- [📸 Galeria](#-galeria)
- [⚠️ Notas Importantes](#️-notas-importantes)

---

## 🎮 Multiplayer LAN

O sistema de multiplayer LAN foi completamente reformulado para oferecer uma experiência co-op estável e fluida.

### ✅ Funcionalidades Implementadas

| Feature | Descrição |
|---------|-----------|
| **Sincronização de Sprites** | Animações dos jogadores remotos sincronizadas em tempo real (ataque, caminhada, idle) |
| **Movimentação Fluida** | Interpolação otimizada para movimentação suave dos peers remotos |
| **Companion AI** | Companheiros NPC funcionam corretamente para clientes LAN |
| **Sons Espaciais** | Sons de combate dos peers só tocam quando estão próximos |
| **Chat LAN** | Sistema de chat funcional com suporte multilíngue |
| **Cleanup de Peers** | Avatares fantasma são removidos corretamente ao sair/desconectar |
| **Anti-Serialização** | Peers remotos NÃO são salvos no disco, prevenindo corrupção de save |
| **NPC Sync** | NPCs do mundo não são afetados pelo estado dos peers LAN |

### 🔄 Protocolo de Rede

```
PlayerState (sincronizado a cada tick):
├── Posição (x, y)
├── Animação atual
├── HP perdido (missingHP)
├── Mana
├── Equipamentos visíveis
└── Estado de combate
```

---

## ⚔️ Arena PVP

Um sistema completo de **PVP 1v1** para duelos entre jogadores em sessões LAN.

### 📍 Localização
A Arena PVP fica no **Vale de Lannegar** (`H10`), onde o **Mestre da Arena** aguarda os desafiadores.

### 🎯 Como Funciona

```
┌──────────────────────────────────────────────┐
│  1. Encontre o Mestre da Arena no Vale       │
│  2. Inicie o desafio (ambos os jogadores)    │
│  3. Equipamentos são guardados               │
│  4. Equipamentos PVP são fornecidos          │
│  5. Teleporte para a Arena PVP               │
│  6. LUTE!                                    │
│  7. Vencedor recebe 200 gold + recompensas   │
│  8. Equipamentos originais são devolvidos     │
│  9. Saia pela porta ou use Scroll: Teleport  │
└──────────────────────────────────────────────┘
```

### 🛡️ Equipamentos PVP

Ambos os jogadores recebem equipamento padronizado para garantir fairness:

| Slot | Item |
|------|------|
| Arma | Steel Longsword |
| Escudo | Steel Shield |
| Armadura | Chainmail |
| Consumível | 2x Potion of Healing |

### 🏆 Sistema de Recompensas

| Resultado | Recompensa |
|-----------|-----------|
| 🏆 **Vitória** | 200 gold + Scroll: Teleport + equipamento original recuperado |
| 💀 **Derrota** | Scroll: Teleport + equipamento original recuperado |
| ❌ **Desconexão** | Scroll: Teleport + equipamento original recuperado |

### 🔧 Sincronização de Combate

O sistema de dano PVP utiliza uma abordagem baseada em chat para contornar limitações do protocolo LAN:

- **Detecção de Morte:** Quando o perdedor é eliminado, uma mensagem `[PVP] Player has been eliminated!` é enviada via chat
- **Trigger de Vitória:** O handler de chat no dispositivo do vencedor detecta a mensagem e seta `pvp_arena_won = 1`
- **NPC de Saída:** Reconhece automaticamente o resultado da luta e distribui recompensas
- **Saída Dupla:** Porta física na arena (transition zone) + Scroll: Teleport como backup

### 📊 Variáveis de Controle

| Variável | Valor | Significado |
|----------|-------|-------------|
| `pvp_arena_won` | `0` | Perdedor |
| `pvp_arena_won` | `1` | Vencedor |
| `pvp_arena_won` | `2` | Luta em andamento |
| `pvp_fight_active` | `0` | Sem luta ativa |
| `pvp_fight_active` | `1` | Luta em andamento |

---

## 🧙 NPCs & Questlines Exclusivos

### 🎭 Furulipo — O Mistério do Caçador de Relíquias

Um NPC misterioso que aparece em múltiplas localizações do mapa.

| Localização | Nome Exibido | Descrição |
|-------------|-------------|-----------|
| **Kingsbridge** | `???` | Aparece como desconhecido, gerando curiosidade |
| **Demais locais** | `Furulipo` | Nome revelado após o primeiro encontro |

**Questline: A Relíquia Solar**
- Encontre Furulipo em diferentes locais do mundo
- Descubra a história da **Relíquia Solar** e sua conexão com as Cruzadas
- Derrote o boss que guarda a relíquia
- Recompensa: **Medalha da Cruzada Solar** — item equipável único

### ⚔️ Lyssara — Companheira de Batalha

Uma nova companheira recrutável localizada na **Torre de Tremadan**.

| Atributo | Detalhe |
|----------|---------|
| **Localização** | Torre de Tremadan |
| **Classe** | Guerreira |
| **Retrato** | Retrato personalizado registrado |
| **Recrutamento** | Via diálogo após completar pré-requisitos |

### 🏟️ Mestre da Arena PVP

| Atributo | Detalhe |
|----------|---------|
| **Localização** | Vale de Lannegar (H10) |
| **Função** | Gerencia duelos PVP entre jogadores LAN |
| **Retrato** | #119 |
| **Sprite** | `male_black_1` |

---

## 🎨 Interface Medieval

A interface do lobby LAN e do chat foi completamente redesenhada com tema medieval dark fantasy.

### 🖌️ Elementos Visuais

| Componente | Estilo |
|------------|--------|
| **Background** | Gradientes escuros com tons de cobre/bronze |
| **Botões** | Bordas douradas com efeito 3D medieval |
| **Painéis** | Texturas de pergaminho com bordas ornamentais |
| **Diálogos** | Design de janela medieval com cantos arredondados |
| **Chat** | Balões temáticos com fonte medieval |

### 📐 Implementação

- Todos os estilos são gerados **programaticamente** via Android `GradientDrawable`
- Sem dependência de assets de imagem externos
- Compatível com todos os tamanhos de tela
- Otimizado para 4-bit registers do Dalvik

---

## 📦 Sistema de Loot Aprimorado

Os containers interativos do mundo agora possuem tabelas de loot temáticas e balanceadas.

### 🎲 Containers Suportados

| Container | Tema | Melhores Drops |
|-----------|------|----------------|
| 🪑 **Mesas** | Comida, ferramentas | Poções, Scrolls |
| 📚 **Estantes** | Conhecimento arcano | Scrolls de Sabedoria |
| 🛢️ **Barris** | Provisões, bebidas | Ale, Vinho, Rum |
| 💀 **Cadáveres** | Pertences pessoais | Armas, Poções |
| 📦 **Caixotes** | Suprimentos de viagem | Poções, Armas |
| 📦 **Baús Grandes** | Loot recompensador | Armas de Aço, Poções avançadas |
| 📦 **Baús Pequenos** | Loot básico | Poções, Scrolls |
| ⚰️ **Sarcófagos** | Tesouro antigo | Poções de Death Ward |
| 💀 **Restos Esqueléticos** | Restos de guerreiros | Armas, Crânios |
| 🐣 **Ninhos** | Materiais animais | Ovos, Gordura |
| 🌳 **Árvores** | Frutos naturais | Golden Apple |
| ⛪ **Altares** | Bênçãos divinas | Scrolls sagrados |
| 👑 **Tronos** | Itens reais/raros | Poções de Heroísmo |
| 🕳️ **Buracos** | Itens escondidos | Poções, Scrolls |

### ⚖️ Filosofia de Balanceamento

- 🟢 **Itens comuns** (poções básicas, scrolls de recall): 15-30% de chance
- 🟡 **Itens médios** (armas de ferro/aço, poções intermediárias): 5-12%
- 🔴 **Itens raros** (scrolls de invocação, poções de heroísmo): 3-8%
- ❌ **Nenhuma arma mágica/encantada** — preserva a progressão natural do jogo
- ❌ **Nenhum item de quest** é incluído nos drops

---

## 🌍 Idiomas Suportados

| Idioma | Status |
|--------|--------|
| 🇺🇸 English | ✅ Completo |
| 🇪🇸 Español | ✅ Completo |
| 🇧🇷 Português (Brasil) | ✅ Completo |
| 🇷🇺 Русский | ✅ Base |
| 🇩🇪 Deutsch | ✅ Base |
| 🇵🇱 Polski | ✅ Base |
| 🇨🇿 Čeština | ✅ Base |

> **Nota:** Todos os NPCs exclusivos, questlines e diálogos da Arena PVP possuem traduções completas em EN, ES e PT-BR. Os demais idiomas utilizam as strings base do jogo.

---

## 🔧 Correções Técnicas

### 🐛 Bugs Corrigidos

| Bug | Causa | Solução |
|-----|-------|---------|
| **Crash: VerifyError** | Registradores Dalvik fora do range (v8 em método .locals 8) | Refatorado para usar v7+v4 dentro do limite |
| **Ghost Players** | Peer actors persistiam após desconexão | `clearPeerActors()` chamado no cleanup |
| **Save Corruption** | Peers NPC eram serializados no save | Filtro `lanPeerVisual` no processo de save |
| **NPC Clone Bug** | NPCs mundiais duplicados como "Soldier" | Prevenido flag `ai_disabled` em NPCs normais |
| **Loading Freeze** | `travel#H10,1` sem entry point | Entry point + transition zone física |
| **Wrong Dialogue** | Perdedor via mensagem de disconnect | Reordenação de conditions no diálogo |
| **NullPointerException** | TextureRegion nula no SpriteBatch.draw | Inicialização garantida do TextureRegion |
| **Container Crash** | Loot tables malformadas | Restauração completa dos dados de rules |
| **Deadlock** | Sincronização de pausa no render thread | Otimização do `forcePublishLocalState()` |

### 📁 Arquivos Chave Modificados

<details>
<summary><b>Smali (Bytecode)</b></summary>

| Arquivo | Propósito |
|---------|-----------|
| `Player.smali` | Death handler PVP, publicação de estado |
| `LanSessionManager.smali` | PVP elimination detection (host + client) |
| `LanGameBridge.smali` | Sincronização de combate |
| `LanLobbyActivity.smali` | UI medieval do lobby |
| `LanGameBridgeChatRunnable.smali` | UI medieval do chat |
| `NPC.smali` | Filtro de serialização para peers |

</details>

<details>
<summary><b>Conversas & Quests</b></summary>

| Arquivo | Propósito |
|---------|-----------|
| `pvp_arena_master.txt` | Diálogo do NPC que inicia duelos PVP |
| `pvp_arena_exit.txt` | Diálogo do NPC de saída da arena (vencedor/perdedor) |
| `furulipo_*.txt` | Questline do Furulipo (múltiplas conversas) |
| `lyssara_*.txt` | Recrutamento e diálogos da Lyssara |

</details>

<details>
<summary><b>Mapas TMX</b></summary>

| Arquivo | Propósito |
|---------|-----------|
| `H10.tmx` | Adicionado Arena Master NPC + entry point |
| `H10_pvp_arena.tmx` | Mapa da arena PVP (entries, NPC, transition zone) |

</details>

---

## ⚠️ Notas Importantes

> **Requisitos para PVP:**
> - Ambos os jogadores devem estar na mesma rede WiFi/LAN
> - Recomendado já ter visitado **Kingsbridge** antes de jogar PVP (o Scroll: Teleport usa cidades visitadas)
> - O PVP é 1v1 — ambos os jogadores devem iniciar o desafio com o Mestre da Arena

> **Compatibilidade:**
> - Android 5.0+ (API 21+)
> - Baseado no Exiled Kingdoms versão multiplayer
> - Saves existentes são compatíveis

> **Limitações Conhecidas:**
> - O dano PVP é calculado localmente por cada dispositivo
> - Latência da rede pode causar pequenos delays na sincronização de HP
> - O Scroll: Teleport pode não funcionar em algumas áreas seladas magicamente (comportamento vanilla)

---

<div align="center">

### 🛡️ Construído com ☕ e ⚔️

*Baseado em Exiled Kingdoms por 4 Dimension Games*  
*Mod desenvolvido com auxílio de engenharia reversa Smali/Dalvik*

---

**[⬇️ Download APK](link)** · **[🐛 Reportar Bug](link)** · **[💬 Discussão](link)**

</div>
]]>
