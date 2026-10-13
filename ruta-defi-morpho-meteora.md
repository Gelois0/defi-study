# DeFi: ruta de estudio para Morpho y Meteora DLMM

**Objetivo:** entender operaciones DeFi — préstamos on-chain y provisión de liquidez/market making automatizado — sin confundirlas con trading direccional.

- **Morpho:** lending y crédito on-chain.
- **Meteora DLMM:** provisión de liquidez concentrada por bins y market making automatizado.

> Esta ruta es educativa. No recomienda depositar ni abrir posiciones.

## Secuencia de estudio

### Fase 1 — Contexto de pagos y dinero digital (complementaria)

Estos recursos ayudan a conectar pagos tradicionales, stablecoins y finanzas digitales. Son contexto, no prerrequisito para estudiar Morpho o Meteora.

1. **The Anatomy of the Swipe — Ahmed Siddiqui**
   - Aprender: issuing, acquiring, autorización, clearing, settlement, chargebacks y redes de tarjetas.
   - Relevancia: permite comparar pagos tradicionales con tarjetas cripto y settlement on-chain.
   - [Sitio del libro](https://www.academyoftheswipe.com/order-book)

2. **Decoding Digital Assets** — *Distinguishing the Dream from the Dystopia in Stablecoins, Tokenized Deposits, and Central Bank Digital Currencies*
   - Aprender: stablecoins, depósitos tokenizados, CBDC, custodia, interoperabilidad y riesgos regulatorios.
   - [Springer](https://link.springer.com/book/10.1007/978-3-031-54601-3)

### Fase 2 — Fundamentos selectivos de Ethereum y DeFi

3. **Mastering Ethereum, 2nd Edition**
   - Lectura selectiva: cuentas y wallets, transacciones, gas, tokens, contratos, firmas, permisos, oráculos y seguridad EVM.
   - Relevancia para Morpho: entender contratos, mercados, vaults, oráculos, LLTV, permisos de curator/allocator y liquidaciones.
   - [Libro y repositorio](https://github.com/ethereumbook/ethereumbook)

4. **Decentralizing Finance — Kenneth Bok**
   - Aprender: infraestructura DeFi, lending, activos digitales, stablecoins, DLT y conexiones con finanzas tradicionales.
   - [Wiley](https://www.wiley.com/en-ca/Decentralizing+Finance:+How+DeFi,+Digital+Assets,+and+Distributed+Ledger+Technology+Are+Transforming+Finance-p-9781394154975)

5. **Blockchain, Crypto and DeFi**
   - Aprender: Aave, lending, AMM, pools de liquidez, riesgos y ejercicios financieros.
   - [O’Reilly](https://www.oreilly.com/library/view/blockchain-crypto-and/9781394275892/)

### Fase 3 — Morpho: lending y gestión de vaults

6. **Documentación oficial de Morpho**

   Leer en este orden:
   1. [Morpho Blue](https://docs.morpho.org/learn/concepts/blue/)
   2. [Vault V2](https://docs.morpho.org/learn/concepts/vault-v2/)
   3. [Curators](https://docs.morpho.org/learn/concepts/curator/)
   4. [Liquidaciones](https://docs.morpho.org/learn/concepts/liquidation/)
   5. [Recompensas](https://docs.morpho.org/learn/concepts/rewards/)
   6. [Riesgos](https://docs.morpho.org/learn/resources/risks/)

   **Antes de considerar un depósito:** identifica activo, red y contrato; curator, owner y allocator; markets y caps; colateral, oráculo y LLTV; APY base frente a incentivos; liquidez real de retiro; fees y permisos administrativos. Si luego decides probar, usa un monto pequeño y verifica el retiro antes de ampliar.

### Fase 4 — Market making y Meteora DLMM

7. **Trading and Exchanges — Larry Harris**
   - Lectura selectiva: market making, spreads, inventario, arbitraje, liquidez y selección adversa.
   - Relevancia: un LP cobra fees, pero también gestiona inventario y puede quedar expuesto a flujo informado o movimientos fuertes del precio.
   - [Oxford University Press](https://global.oup.com/academic/product/trading-and-exchanges-9780195144703)

8. **Documentación oficial de Meteora DLMM**

   Leer en este orden:
   1. [Qué es DLMM](https://docs.meteora.ag/core-products/dlmm/what-is-dlmm)
   2. [Estrategias y casos de uso](https://docs.meteora.ag/core-products/dlmm/strategies-and-use-cases)
   3. [Modo de cobro de fees](https://docs.meteora.ag/core-products/dlmm/collect-fee-mode)
   4. [Auditorías DLMM](https://docs.meteora.ag/resources/audits/dlmm)

   **Antes de abrir una posición:** confirma pool y contratos oficiales, volumen y liquidez del bin activo, bin step, rango y estrategia (Spot, Curve o BidAsk). Calcula la composición de la posición ante subidas y bajadas; compara fees realizados con impermanent loss, incentivos, fee del gestor y costes de rebalanceo. Si hay vault o bot, revisa permisos y auditoría.

## Preguntas que debes poder responder

### Morpho

- ¿Qué contrato y mercado intervienen? ¿Quién es el curator, owner y allocator?
- ¿Qué colateral, oráculo, LLTV y caps aplican?
- ¿Cuál es el rendimiento base y qué parte son incentivos?
- ¿Hay liquidez de salida suficiente? ¿Qué escenarios producen liquidación o bad debt?

### Meteora DLMM

- ¿Cuál es el bin activo y el bin step?
- ¿Qué estrategia se usa: Spot, Curve o BidAsk?
- Si el precio sube o baja, ¿en qué token queda la posición?
- ¿Los fees netos compensan impermanent loss y costes de gestión?
- ¿El APY refleja fees realizados o incentivos temporales?

## Fórmulas para comparar resultados

```text
DLMM neto = fees de swaps + incentivos realizados
            − impermanent loss − fee del gestor − gas/rebalanceos

Lending neto = interés de borrowers + incentivos realizados
               − fee del vault − pérdidas por bad debt/depeg − gas
```

Son marcos de análisis, no modelos completos: define horizonte, unidades, método para estimar impermanent loss y tratamiento de incentivos antes de comparar.

## Secuencia práctica prudente

1. Estudiar pagos, stablecoins, Ethereum y DeFi a nivel conceptual.
2. Analizar vaults y mercados de Morpho sin depositar.
3. Si decides probar, hacer un depósito pequeño y comprobar un retiro parcial.
4. Observar pools Meteora y simular cambios de precio, sin abrir posición.
5. Si decides probar, empezar pequeño en un par líquido y con un rango que comprendas.
6. Comparar el resultado neto con mantener los activos fuera del protocolo.

No conectes una wallet ni firmes transacciones hasta verificar el flujo completo, la red, el contrato, los permisos y la ruta de salida.
