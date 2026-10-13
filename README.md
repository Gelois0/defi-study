# DeFi

Recursos en español para estudiar finanzas descentralizadas: préstamos, provisión de liquidez, stablecoins, ejecución y riesgos.

**No hay una ruta ni un orden obligatorio.** Consulta los temas que necesites y aporta correcciones o recursos mediante issues y pull requests.

## Temas

- [Préstamos: Morpho](#préstamos-morpho)
- [Liquidez y market making: Meteora DLMM](#liquidez-y-market-making-meteora-dlmm)
- [Stablecoins](#stablecoins)
- [Ethereum: infraestructura para DeFi](#ethereum-infraestructura-para-defi)
- [Datos y verificación](#datos-y-verificación)
- [MEV, ejecución y privacidad](#mev-ejecución-y-privacidad)
- [Libros y lecturas](#libros-y-lecturas)

## Préstamos: Morpho

**Qué estudiar:** mercados, vaults, colateral, oráculos, LLTV, liquidaciones y gestión de riesgos.

- [Morpho Blue](https://docs.morpho.org/learn/concepts/blue/)
- [Vault V2](https://docs.morpho.org/learn/concepts/vault-v2/)
- [Curators](https://docs.morpho.org/learn/concepts/curator/)
- [Liquidaciones](https://docs.morpho.org/learn/concepts/liquidation/)
- [Recompensas](https://docs.morpho.org/learn/concepts/rewards/)
- [Riesgos](https://docs.morpho.org/learn/resources/risks/)

**Para analizar un mercado o vault:** identifica red y contrato, curator/owner/allocator, mercados y caps, colateral, oráculo y LLTV. Separa el interés base de los incentivos; revisa fees, permisos administrativos y liquidez de retiro.

## Liquidez y market making: Meteora DLMM

**Qué estudiar:** bins, bin step, rango, fees, inventario y estrategias Spot, Curve y BidAsk.

- [Qué es DLMM](https://docs.meteora.ag/core-products/dlmm/what-is-dlmm)
- [Estrategias y casos de uso](https://docs.meteora.ag/core-products/dlmm/strategies-and-use-cases)
- [Modo de cobro de fees](https://docs.meteora.ag/core-products/dlmm/collect-fee-mode)
- [Auditorías](https://docs.meteora.ag/resources/audits/dlmm)

**Para analizar una posición:** identifica el bin activo, la liquidez y el volumen, y calcula en qué token queda la posición si el precio sube o baja. Compara fees realizados con impermanent loss y costes de gestión. Si hay un vault o bot, revisa sus permisos.

### Comparación de resultados

```text
DLMM neto = fees de swaps + incentivos realizados
            − impermanent loss − fee del gestor − gas/rebalanceos

Lending neto = interés de borrowers + incentivos realizados
               − fee del vault − pérdidas por bad debt/depeg − gas
```

Son esquemas orientativos, no modelos completos. Define horizonte, moneda de valoración y referencia de comparación —por ejemplo, mantener los activos— para evitar mezclar métricas o contabilizar pérdidas dos veces.

## Stablecoins

Subtema de DeFi: emisión, reservas, canje, custodia, redes y riesgos. Las páginas del emisor describen sus propios productos y afirmaciones; no constituyen por sí solas prueba independiente de solvencia o adopción.

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

**Preguntas de análisis:** ¿quién emite el activo?, ¿qué derecho de canje existe?, ¿qué reservas o colateral lo respaldan?, ¿qué controles de congelamiento aplican?, ¿cuál es el contrato oficial y en qué red se utiliza?

## Ethereum: infraestructura para DeFi

Referencia técnica de apoyo, no una ruta de programación ni el eje de todo el repositorio.

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

## Datos y verificación

- [Etherscan](https://etherscan.io/) — contratos, transferencias y eventos.
- [Etherscan API](https://docs.etherscan.io/)
- [DefiLlama — Stablecoins](https://defillama.com/stablecoins)
- [DefiLlama — Stablecoins por red](https://defillama.com/stablecoins/chains)
- [Dune](https://dune.com/browse/dashboards)

La oferta de stablecoins no equivale a volumen de pagos, y la distribución por red no demuestra liquidez local ni acceso a off-ramp. Revisa periodo y metodología antes de citar métricas.

## MEV, ejecución y privacidad

- [MEV — Ethereum](https://ethereum.org/developers/docs/mev/)
- [Flashbots Protect](https://docs.flashbots.net/flashbots-protect/overview)
- [Flashbots Protect — integración](https://docs.flashbots.net/flashbots-protect/quick-start)
- [MEV Blocker](https://docs.mevblocker.io/)
- [MEV Blocker — endpoints](https://docs.mevblocker.io/mevblocker/users-and-integrators/users/available-endpoints)
- [Privacidad en Ethereum](https://ethereum.org/privacy/ethereum/)
- [Hoja de ruta de privacidad](https://ethereum.org/roadmap/privacy/)

**Envío privado no significa privacidad en la cadena:** ocultar una transacción del mempool público antes de incluirla no oculta automáticamente sus datos después de la inclusión.

Lecturas pendientes de evaluación crítica:

- [Maximal Extractable Value Book — Monoceros](https://www.monoceros.com/insights/maximal-extractable-value-book)
- [PropAMM Shenanigans — 0x](https://0x.org/post/propamm-shenanigans)
- [Proprietary AMMs and Ethereum — ethresear.ch](https://ethresear.ch/t/proprietary-amms-and-ethereum/25543)

## Libros y lecturas

Selección por tema, sin secuencia obligatoria:

| Recurso | Tema |
| --- | --- |
| [Decentralizing Finance — Kenneth Bok](https://www.wiley.com/en-ca/Decentralizing+Finance:+How+DeFi,+Digital+Assets,+and+Distributed+Ledger+Technology+Are+Transforming+Finance-p-9781394154975) | Infraestructura DeFi, lending y conexión con finanzas tradicionales. |
| [Blockchain, Crypto and DeFi](https://www.oreilly.com/library/view/blockchain-crypto-and/9781394275892/) | Lending, AMM, pools y riesgos. |
| [Trading and Exchanges — Larry Harris](https://global.oup.com/academic/product/trading-and-exchanges-9780195144703) | Market making, inventario, spreads y selección adversa. |
| [Mastering Ethereum, 2nd Edition](https://github.com/ethereumbook/ethereumbook) | Cuentas, contratos, tokens, gas y seguridad EVM. |
| [Decoding Digital Assets](https://link.springer.com/book/10.1007/978-3-031-54601-3) | Stablecoins, depósitos tokenizados y CBDC. |
| [The Anatomy of the Swipe — Ahmed Siddiqui](https://www.academyoftheswipe.com/order-book) | Contexto complementario: pagos con tarjeta y settlement. |

## Colaborar

Cualquiera puede proponer recursos, corregir enlaces o mejorar las explicaciones mediante **issues y pull requests**. Consulta [cómo contribuir](CONTRIBUTING.md).

Este material es educativo: no recomienda inversiones ni promete rendimientos. Antes de interactuar con un protocolo, verifica activo, red, contrato, permisos, costes y salida. No compartas secretos ni datos privados.

## Licencia

[MIT](LICENSE). Los libros y recursos externos conservan sus respectivas licencias; aquí se enlazan, no se redistribuyen.
