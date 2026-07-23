# Plano de otimização de mídia

## Contexto

O site já passou por correções de HTML, SEO, acessibilidade, limpeza de assets e melhorias comerciais. A próxima frente de performance é reduzir o peso das mídias públicas, principalmente dos GIFs animados, preservando o funcionamento e a aparência atuais.

Este documento prepara uma futura etapa de conversão. Nenhum arquivo de mídia é convertido, substituído ou removido nesta fase.

## Regras de segurança

- Não alterar ou expor a página assistencial preservada.
- Não otimizar `img/png/nelcy.png` sem autorização separada.
- Não incluir arquivos protegidos em testes públicos ou em documentação com detalhes sensíveis.
- Não publicar diretamente sem validação visual e aprovação.

## Inventário atual de mídia pública

Os seis GIFs abaixo são públicos, estão em uso e possuem referência nas páginas indicadas. Os tamanhos são aproximados, calculados a partir dos arquivos atuais.

| Arquivo | Página(s) onde aparece | Tamanho aproximado | Formato atual | Uso no site | Prioridade de otimização |
| --- | --- | ---: | --- | --- | --- |
| `img/gif/heitor.gif` | `index.html` | 821 KiB | GIF animado | Animação da página inicial | Alta |
| `img/gif/atendimento.gif` | `saibaAtendimento.html` | 678 KiB | GIF animado | Animação do serviço de atendimento | Alta |
| `img/gif/hdrive.gif` | `saibaBackup.html` | 594 KiB | GIF animado | Animação do serviço de backup | Alta |
| `img/gif/macintosh.gif` | `saibaApple.html` | 573 KiB | GIF animado | Animação do serviço para equipamentos Apple | Alta |
| `img/gif/color.gif` | `saibaCalibracao.html` | 195 KiB | GIF animado | Animação do serviço de calibração | Média |
| `img/gif/windows.gif` | `saibaWindows.html` | 69 KiB | GIF animado | Animação do serviço para Windows | Média |

O diretório `img/gif` ocupa atualmente cerca de 2,86 MiB. Além dos GIFs, o inventário de `img` contém arquivos PNG e SVG, que permanecem sem alterações nesta etapa.

### Asset protegido e itens fora do escopo

Há um asset protegido preservado em `img/png/nelcy.png`. Ele está fora do escopo e não deve ser aberto, descrito, testado publicamente ou otimizado sem autorização separada.

Também ficam fora do escopo desta etapa:

- todos os arquivos PNG e SVG;
- todos os arquivos em `fonts`;
- os GIFs originais, que serão apenas avaliados para conversão em uma próxima branch.

As fontes atuais são somente `SourceCodePro-Regular.ttf` e `SourceCodePro-SemiBold.ttf`, ambas da família Source Code Pro, e devem ser preservadas.

## Estratégia recomendada

### 1. WebP animado

- Mantém o uso com `<img>` ou `<picture>`.
- Exige uma mudança menor no HTML.
- Possui boa compatibilidade em navegadores modernos.
- Pode reduzir bastante o peso em comparação com GIF.

### 2. MP4/WebM

- Normalmente gera arquivos menores.
- Exige trocar `<img>` por `<video>`.
- Exige cuidado com `autoplay`, `muted`, `loop`, `playsinline` e acessibilidade.
- Pode ser melhor para animações decorativas grandes.

## Decisão recomendada para este site

Adotar uma abordagem conservadora:

1. Na primeira rodada, converter os GIFs públicos usados para WebP animado.
2. Manter os GIFs originais temporariamente como fallback ou até a conclusão da validação.
3. Avaliar MP4/WebM somente se o WebP não produzir redução suficiente.
4. Não alterar o asset protegido.
5. Não alterar nem converter as fontes nesta etapa.

## Nomes sugeridos para arquivos otimizados

| Arquivo atual | Nome final sugerido |
| --- | --- |
| `img/gif/heitor.gif` | `img/webp/heitor.webp` |
| `img/gif/atendimento.gif` | `img/webp/atendimento.webp` |
| `img/gif/hdrive.gif` | `img/webp/hdrive.webp` |
| `img/gif/macintosh.gif` | `img/webp/macintosh.webp` |
| `img/gif/color.gif` | `img/webp/color.webp` |
| `img/gif/windows.gif` | `img/webp/windows.webp` |

Esses arquivos e o diretório `img/webp` são apenas sugestões e não devem ser criados nesta etapa.

## Ferramentas possíveis

- FFmpeg.
- ImageMagick.
- Ferramentas online confiáveis, desde que não sejam usadas com arquivos sensíveis ou protegidos.
- Conversão fora do repositório antes de substituir qualquer asset.

Nenhuma ferramenta deve ser instalada como parte desta etapa de planejamento.

## Checklist futura de conversão

- [ ] Criar uma branch específica para a conversão.
- [ ] Instalar ou confirmar a ferramenta escolhida.
- [ ] Converter um GIF por vez.
- [ ] Comparar o tamanho original com o otimizado.
- [ ] Atualizar o HTML somente após validar o arquivo convertido.
- [ ] Validar o resultado em desktop e mobile.
- [ ] Validar acessibilidade, incluindo comportamento de animações.
- [ ] Confirmar que não há referência quebrada.
- [ ] Fazer um commit separado para a conversão.
- [ ] Não fazer push antes da aprovação visual.

## Critérios de aceite

- Redução significativa no peso total de `img/gif`.
- Visual preservado.
- Sem quebra de layout.
- Sem exposição de página ou asset protegido.
- Sem referências quebradas.
- Validação pública após o push aprovado.
