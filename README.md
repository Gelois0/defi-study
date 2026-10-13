# DeFi

Recursos en español sobre finanzas descentralizadas: lending, provisión de liquidez, stablecoins, ejecución y riesgos. El repositorio es temático: **no impone una ruta ni un orden obligatorio de estudio**.

## Índice

- [1. Préstamos y mercados: Morpho](#1-préstamos-y-mercados-morpho)
  - [Aave V3](#aave-v3)
- [2. Liquidez y market making: Meteora DLMM](#2-liquidez-y-market-making-meteora-dlmm)
  - [Comparación de resultados](#comparación-de-resultados)
- [3. Stablecoins](#3-stablecoins)
  - [USDC / Circle](#usdc--circle)
  - [USDT / Tether](#usdt--tether)
  - [DAI / USDS / Sky](#dai--usds--sky)
- [4. Ethereum: infraestructura para DeFi](#4-ethereum-infraestructura-para-defi)
  - [Red y transacciones](#red-y-transacciones)
  - [Tokens, wallets y permisos](#tokens-wallets-y-permisos)
  - [Consulta técnica](#consulta-técnica)
- [5. Datos y verificación](#5-datos-y-verificación)
- [6. MEV, ejecución y privacidad](#6-mev-ejecución-y-privacidad)
- [7. Libros y lecturas](#7-libros-y-lecturas)
- [8. Colaborar](#8-colaborar)
- [9. Licencia](#9-licencia)

---

## 1. Préstamos y mercados: Morpho

**Enfoque:** lending on-chain, mercados, vaults, colateral, oráculos, LLTV, liquidaciones y gestión de riesgos.

- [Morpho Blue](https://docs.morpho.org/learn/concepts/blue/)
- [Vault V2](https://docs.morpho.org/learn/concepts/vault-v2/)
- [Curators](https://docs.morpho.org/learn/concepts/curator/)
- [Liquidaciones](https://docs.morpho.org/learn/concepts/liquidation/)
- [Recompensas](https://docs.morpho.org/learn/concepts/rewards/)
- [Riesgos](https://docs.morpho.org/learn/resources/risks/)

**Al analizar un mercado o vault**, identifica la red y el contrato; curator, owner y allocator; mercados y caps; colateral, oráculo y LLTV. Separa el interés base de los incentivos y revisa fees, permisos administrativos y liquidez de retiro.

### Aave V3

**Enfoque:** mercados de lending con reservas de liquidez compartidas por activo. Los proveedores reciben aTokens que representan su posición; la deuda se registra en tokens de deuda. El activo subyacente, la red y la instancia del mercado importan: parámetros, liquidez y riesgos pueden diferir entre mercados.

**Fuentes técnicas**

- [Documentación oficial: visión general de Aave V3](https://aave.com/docs/aave-v3/overview)
- [Reservas y parámetros de riesgo](https://aave.com/docs/aave-v3/concepts/reserve)
- [Operaciones de mercado: supply, borrow, repay y withdraw](https://aave.com/docs/aave-v3/markets/operations)
- [Estrategia de tasas de interés](https://aave.com/docs/aave-v3/smart-contracts/interest-rate-strategy)
- [Contrato Pool](https://aave.com/docs/aave-v3/smart-contracts/pool)
- [Repositorio oficial del protocolo](https://github.com/aave-dao/aave-v3-origin) — código, notas de versiones y materiales de seguridad. Los informes de auditoría se refieren a versiones y alcances concretos; no son garantía de seguridad actual.
- [Aave V3 Technical Paper](https://raw.githubusercontent.com/aave/aave-v3-core/master/techpaper/Aave_V3_Technical_Paper.pdf) — documento técnico inicial de 2022; contrastar sus descripciones con la versión desplegada y documentación actual.

**Curso de desarrollo**

- [Aave V3 Protocol Development — Cyfrin Updraft](https://updraft.cyfrin.io/courses/aave-v3) — curso avanzado en inglés orientado a Solidity y Foundry. La página describe arquitectura, reservas, aTokens y deuda, tasas/utilización, supply/borrow/repay/withdraw/liquidation, flash loans e integración de una aplicación; anuncia ejercicios prácticos. La guía de configuración del curso indica que sus ejercicios usan un fork de Ethereum mainnet y se enfocan en el tag v3.3.0: compara ese código con las versiones más recientes antes de reutilizar ejemplos. El contenido exacto y las condiciones de acceso pueden cambiar.

**Lecturas y guías sobre Aave**

- [Aave V3 Book — GitHub](https://github.com/Scannty/aave-v3-book) — guía comunitaria centrada en arquitectura V3, tasas, reservas, liquidaciones y gobernanza. No es documentación oficial; valida cada afirmación frente al código y docs oficiales y comprueba su estado de mantenimiento antes de depender de ella.
- [Aave Book — Calnix / GitBook](https://calnix.gitbook.io/aave-book) — guía técnica complementaria sobre contratos, funciones e interés. Algunas páginas parten de V2 y explican cambios de V3; el propio contenido advierte que una parte de la arquitectura ilustrada corresponde a V2, y varias páginas indican que no se actualizan desde hace años. Úsala como lectura histórica, no como especificación vigente.
- [DeFi and the Future of Finance — Harvey, Ramachandran y Santoro](https://www.wiley.com/en-us/DeFi+and+the+Future+of+Finance-p-9781119836025) — libro de fundamentos y análisis de protocolos; incluye Aave entre los casos de lending. Complementa, no sustituye, documentación de V3.
- [Blockchain, Crypto and DeFi — Marco Di Maggio](https://www.wiley.com/en-us/Blockchain%2C+Crypto+and+DeFi%3A+Bridging+Finance+and+Technology-p-9781394275892) — perspectiva financiera y técnica con casos sobre lending/DeFi; útil como contexto, no como manual actualizado de contratos Aave.

**Cómo profundizar en la mecánica**

1. **Flujo y contabilidad:** sigue un supply desde transferencia del token hasta acuñación del aToken; después rastrea cómo un borrow crea deuda y entrega liquidez, y cómo repay y withdraw alteran ambos balances. No confundas el aToken con el activo subyacente ni la tasa mostrada con un rendimiento garantizado.
2. **Tasas y liquidez:** la utilización del reserve afecta las tasas de borrow; el modelo de dos pendientes eleva la tasa más rápido al rebasar el punto óptimo para incentivar repago/supply y conservar liquidez. La tasa del proveedor depende de la actividad de borrow y del reserve factor; incentivos externos son otra fuente y deben separarse.
3. **Colateral y liquidación:** distingue LTV (capacidad inicial de endeudamiento), liquidation threshold (umbral de liquidación) y liquidation bonus/penalty (incentivo/coste de liquidar). El Health Factor combina valor del colateral, umbrales ponderados y deuda: `HF = Σ(valor_colateral_i × umbral_liquidación_i) / deuda_total`. Si cae por debajo de 1, la posición puede ser liquidable; los oráculos, el precio, la deuda acumulada y la liquidez disponible afectan el resultado.
4. **Gestión de riesgo:** estudia caps de supply/borrow, pausas/freeze, eMode y aislamiento donde estén habilitados, riesgo de oráculo, calidad y correlación del colateral, concentración de liquidez, parámetros de gobernanza y diferencias entre redes. No asumas que una función o parámetro se comporta igual en todas las versiones o mercados.
5. **Lectura de código:** parte de la versión del contrato que corresponde al mercado que estás analizando; recorre `Pool` y las bibliotecas de lógica para supply, borrow, repay y liquidation; contrasta la ejecución con eventos y estado on-chain. Una auditoría antigua no cubre automáticamente upgrades posteriores, configuración del mercado ni dependencias externas.

**Preguntas de análisis:** ¿qué activo entra y sale?, ¿quién paga el interés?, ¿cuánta liquidez queda disponible para retiros?, ¿qué precio/oráculo afecta el HF?, ¿qué condiciones activan una liquidación y qué recibe el liquidator?, ¿qué parámetros puede modificar gobernanza?, ¿cuál es la versión exacta del contrato y qué riesgos de red, puente o activo se añaden?

## 2. Liquidez y market making: Meteora DLMM

**Enfoque:** bins, bin step, rango, fees, inventario y estrategias Spot, Curve y BidAsk.

- [Qué es DLMM](https://docs.meteora.ag/core-products/dlmm/what-is-dlmm)
- [Estrategias y casos de uso](https://docs.meteora.ag/core-products/dlmm/strategies-and-use-cases)
- [Modo de cobro de fees](https://docs.meteora.ag/core-products/dlmm/collect-fee-mode)
- [Auditorías](https://docs.meteora.ag/resources/audits/dlmm)

**Recurso complementario:** [LP Army Academy](https://www.lparmy.com/academy) — recurso externo sugerido para aprender sobre provisión de liquidez. El contenido de la página no se ha revisado de forma independiente.

**Al analizar una posición**, identifica el bin activo, la liquidez y el volumen; calcula en qué token queda la posición si el precio se mueve. Compara fees realizados con impermanent loss y costes de gestión. Si se usa un vault o bot, revisa sus permisos.

### Comparación de resultados

```text
DLMM neto = fees de swaps + incentivos realizados
            − impermanent loss − fee del gestor − gas/rebalanceos

Lending neto = interés de borrowers + incentivos realizados
               − fee del vault − pérdidas por bad debt/depeg − gas
```

Son esquemas orientativos, no modelos completos. Define horizonte, moneda de valoración y referencia de comparación —por ejemplo, mantener los activos— para evitar mezclar métricas o contabilizar pérdidas dos veces.

## 3. Stablecoins

Subtema de DeFi: emisión, reservas, canje, custodia, redes y riesgos. Las páginas de un emisor describen sus propios productos y afirmaciones; por sí solas no son prueba independiente de solvencia o adopción.

### USDC / Circle

- [USDC](https://www.circle.com/usdc)
- [Documentación de USDC](https://developers.circle.com/stablecoins/what-is-usdc)
- [Reservas e informes](https://www.circle.com/transparency)
- [CCTP](https://developers.circle.com/stablecoins/cctp-getting-started) — comprobar redes, versión y condiciones.

### USDT / Tether

- [Transparencia](https://tether.to/en/transparency/)
- [Informes de aseguramiento](https://tether.to/en/transparency/#reports) — una atestación no equivale a una auditoría financiera integral.

### DAI / USDS / Sky

- [Sky](https://sky.money/)
- [Documentación de DAI](https://developers.skyeco.com/protocol/tokens/dai/)
- [Documentación del protocolo](https://developers.skyeco.com/)

**Preguntas para evaluar una stablecoin:** ¿quién la emite?, ¿qué derecho de canje existe?, ¿qué reservas o colateral la respaldan?, ¿qué controles de congelamiento aplican?, ¿cuál es el contrato oficial y en qué red se utiliza?

## 4. Ethereum: infraestructura para DeFi

Referencias de apoyo sobre la infraestructura subyacente; no convierten el repositorio en una ruta de programación.

### Red y transacciones

- [Documentación de Ethereum](https://ethereum.org/developers/docs/)
- [Transacciones](https://ethereum.org/developers/docs/transactions/) — gas, nonce, estados y ejecución.
- [EVM](https://ethereum.org/developers/docs/evm/)
- [Escalabilidad](https://ethereum.org/developers/docs/scaling/)
- [L2BEAT](https://l2beat.com/layer2s/summary) — revisar riesgos y madurez, no solo TVL.

### Tokens, wallets y permisos

- [ERC-20](https://eips.ethereum.org/EIPS/eip-20) — `transfer`, `approve` y `transferFrom`.
- [EIP-2612 / Permit](https://eips.ethereum.org/EIPS/eip-2612) — autorizaciones por firma.
- [ERC-4337](https://eips.ethereum.org/EIPS/eip-4337) — smart accounts, bundlers y paymasters.
- [Approvals — Revoke.cash](https://revoke.cash/learn/approvals/what-are-token-approvals)

### Consulta técnica

- [Ethereum Protocol Fellowship](https://epf.wiki/#/eps/intro)
- [Mastering Ethereum — referencia web](https://masteringethereum.xyz/)

## 5. Datos y verificación

- [Etherscan](https://etherscan.io/) — contratos, transferencias y eventos.
- [Etherscan API](https://docs.etherscan.io/)
- [DefiLlama — Stablecoins](https://defillama.com/stablecoins)
- [DefiLlama — Stablecoins por red](https://defillama.com/stablecoins/chains)
- [Dune](https://dune.com/browse/dashboards)

La oferta de stablecoins no equivale a volumen de pagos, y la distribución por red no demuestra liquidez local ni acceso a off-ramp. Revisa periodo y metodología antes de citar métricas.

## 6. MEV, ejecución y privacidad

- [MEV — Ethereum](https://ethereum.org/developers/docs/mev/)
- [Flashbots Protect](https://docs.flashbots.net/flashbots-protect/overview)
- [Flashbots Protect — integración](https://docs.flashbots.net/flashbots-protect/quick-start)
- [MEV Blocker](https://docs.mevblocker.io/)
- [MEV Blocker — endpoints](https://docs.mevblocker.io/mevblocker/users-and-integrators/users/available-endpoints)
- [Privacidad en Ethereum](https://ethereum.org/privacy/ethereum/)
- [Hoja de ruta de privacidad](https://ethereum.org/roadmap/privacy/)

> **Envío privado no significa privacidad en la cadena:** ocultar una transacción del mempool público antes de incluirla no oculta automáticamente sus datos después de la inclusión.

Lecturas pendientes de evaluación crítica:

- [Maximal Extractable Value Book — Monoceros](https://www.monoceros.com/insights/maximal-extractable-value-book)
- [PropAMM Shenanigans — 0x](https://0x.org/post/propamm-shenanigans)
- [Proprietary AMMs and Ethereum — ethresear.ch](https://ethresear.ch/t/proprietary-amms-and-ethereum/25543)

## 7. Libros y lecturas

Selección por tema, sin secuencia obligatoria:

| Recurso | Tema |
| --- | --- |
| [Decentralizing Finance — Kenneth Bok](https://www.wiley.com/en-ca/Decentralizing+Finance:+How+DeFi,+Digital+Assets,+and+Distributed+Ledger+Technology+Are+Transforming+Finance-p-9781394154975) | Infraestructura DeFi, lending y conexión con finanzas tradicionales. |
| [Blockchain, Crypto and DeFi](https://www.oreilly.com/library/view/blockchain-crypto-and/9781394275892/) | Lending, AMM, pools y riesgos. |
| [Trading and Exchanges — Larry Harris](https://global.oup.com/academic/product/trading-and-exchanges-9780195144703) | Market making, inventario, spreads y selección adversa. |
| [Mastering Ethereum, 2nd Edition](https://github.com/ethereumbook/ethereumbook) | Cuentas, contratos, tokens, gas y seguridad EVM. |
| [Decoding Digital Assets](https://link.springer.com/book/10.1007/978-3-031-54601-3) | Stablecoins, depósitos tokenizados y CBDC. |
| [The Anatomy of the Swipe — Ahmed Siddiqui](https://www.academyoftheswipe.com/order-book) | Contexto complementario: pagos con tarjeta y settlement. |

## 8. Colaborar

Cualquiera puede proponer recursos, corregir enlaces o mejorar las explicaciones mediante **issues y pull requests**. Consulta [cómo contribuir](CONTRIBUTING.md).

Este material es educativo: no recomienda inversiones ni promete rendimientos. Antes de interactuar con un protocolo, verifica activo, red, contrato, permisos, costes y salida. No compartas secretos ni datos privados.

## 9. Licencia

[MIT](LICENSE). Los libros y recursos externos conservan sus respectivas licencias; aquí se enlazan, no se redistribuyen.
