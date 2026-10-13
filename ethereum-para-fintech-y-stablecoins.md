# Ethereum para fintech y stablecoins

Colección de recursos para entender transacciones, redes, stablecoins, verificación on-chain, MEV y privacidad en Ethereum.

> **Alcance:** infraestructura y flujos financieros. No es una ruta de programación ni una recomendación de inversión. Los enlaces son puntos de partida; verifica disponibilidad, términos y versiones vigentes antes de tomar decisiones operativas.

## 1. Fundamentos: red, transacciones y L2

- [Documentación de Ethereum](https://ethereum.org/developers/docs/) — mapa general de la infraestructura.
- [Transacciones](https://ethereum.org/developers/docs/transactions/) — gas, nonce, estados, fees y ejecución.
- [EVM](https://ethereum.org/developers/docs/evm/) — qué ejecuta un contrato y qué implica una interacción on-chain.
- [Escalabilidad](https://ethereum.org/developers/docs/scaling/) — L1, L2 y fundamentos operativos de los rollups.
- [L2BEAT](https://l2beat.com/layer2s/summary) — análisis independiente de L2, riesgos, madurez y TVL. No uses rankings o TVL por sí solos para elegir una red.

## 2. Tokens, wallets y autorizaciones

- [EIP-20 / ERC-20](https://eips.ethereum.org/EIPS/eip-20) — estándar de tokens: `transfer`, `approve`, `transferFrom` y eventos.
- [EIP-2612 / Permit](https://eips.ethereum.org/EIPS/eip-2612) — autorizaciones por firma, UX y riesgo de permisos.
- [ERC-4337 / Account Abstraction](https://eips.ethereum.org/EIPS/eip-4337) — smart accounts y dependencias de bundlers y paymasters.
- [Revoke.cash: qué son las approvals](https://revoke.cash/learn/approvals/what-are-token-approvals) — explicación práctica de las autorizaciones de tokens. Comprueba el contrato y la red antes de revocar.

## 3. Emisores y documentación de stablecoins

Las páginas del emisor son fuentes primarias para conocer sus propios productos y afirmaciones. No las tomes, por sí solas, como prueba independiente de solvencia, adopción o disponibilidad en un país.

### Circle / USDC

- [USDC — Circle](https://www.circle.com/usdc) — producto y disponibilidad declarada por el emisor.
- [Qué es USDC — Circle Docs](https://developers.circle.com/stablecoins/what-is-usdc) — emisión, reservas, CCTP y redes según la documentación de Circle.
- [Circle Transparency](https://www.circle.com/transparency) — informes y atestaciones publicados por Circle.
- [CCTP](https://developers.circle.com/stablecoins/cctp-getting-started) — transferencia nativa de USDC entre redes soportadas; confirma redes, versión, límites y condiciones antes de asumir compatibilidad.

### Tether / USDT

- [Tether Transparency](https://tether.to/en/transparency/) — composición de reservas e información publicada por el emisor.
- [Tether Assurance Opinions](https://tether.to/en/transparency/#reports) — informes publicados. Una atestación no equivale a una auditoría financiera integral.

### Sky / DAI / USDS

- [Sky Protocol](https://sky.money/) — interfaz y productos del ecosistema.
- [DAI — Sky Docs](https://developers.skyeco.com/protocol/tokens/dai/) — referencia técnica del token.
- [Documentación de Sky](https://developers.skyeco.com/) — módulos, gobernanza y documentación del protocolo.

## 4. Exploración y datos on-chain

- [Etherscan](https://etherscan.io/) — consultar contratos, transferencias, eventos, titulares y transacciones en Ethereum. La etiqueta de una dirección no demuestra su identidad.
- [Etherscan API](https://docs.etherscan.io/) — balances, transferencias, eventos, código verificado y gas; útil para integraciones de lectura. Revisa límites y versión de API.
- [DefiLlama — Stablecoins](https://defillama.com/stablecoins) — oferta, precio y distribución de stablecoins. La oferta no equivale al volumen de pagos.
- [DefiLlama — Stablecoins por red](https://defillama.com/stablecoins/chains) — distribución e influjos por cadena. No prueba liquidez local ni acceso a off-ramp.
- [Dune](https://dune.com/browse/dashboards) — dashboards y queries on-chain. Revisa la query, periodo, etiquetas y metodología antes de citar una métrica.

## 5. MEV, privacidad y transacciones privadas

- [MEV — ethereum.org](https://ethereum.org/developers/docs/mev/) — qué es el valor extraíble y cómo puede afectar ejecución, precio y experiencia del usuario.
- [Flashbots Protect: Overview](https://docs.flashbots.net/flashbots-protect/overview) — envío privado de transacciones y propósito del servicio.
- [Flashbots Protect: Quick Start](https://docs.flashbots.net/flashbots-protect/quick-start) — referencia de integración vía RPC o `eth_sendPrivateTransaction`; no la ejecutes con fondos sin validar la ruta completa.
- [MEV Blocker](https://docs.mevblocker.io/) — documentación de infraestructura RPC privada y protección MEV.
- [MEV Blocker: endpoints](https://docs.mevblocker.io/mevblocker/users-and-integrators/users/available-endpoints) — endpoints y diferencias de condiciones de inclusión y rebates.
- [Privacidad en Ethereum](https://ethereum.org/privacy/ethereum/) — límites de una transacción seudónima y pública después de su inclusión.
- [Hoja de ruta de privacidad de Ethereum](https://ethereum.org/roadmap/privacy/) — enfoques para privacidad de lectura, escritura y pruebas privadas.
- [Maximal Extractable Value Book — Monoceros](https://www.monoceros.com/insights/maximal-extractable-value-book) — recurso sobre MEV; pendiente de lectura y evaluación crítica.

> **Límite importante:** un *private transfer* puede ocultar una transacción del mempool público antes de su inclusión, pero no vuelve privada la transacción en la cadena. Tras incluirse, origen, destino, monto y eventos suelen ser visibles, salvo que se utilicen mecanismos de privacidad adicionales.

## 6. Infraestructura y referencia técnica

- [Ethereum Protocol Fellowship — introducción](https://epf.wiki/#/eps/intro) — material sobre protocolo e infraestructura; referencia complementaria, no prerrequisito de programación.
- [Mastering Ethereum](https://masteringethereum.xyz/) — consulta selectiva para transacciones, cuentas, tokens, contratos, gas y seguridad.

## 7. AMMs propietarios y ejecución

- [PropAMM Shenanigans — 0x](https://0x.org/post/propamm-shenanigans) — análisis de AMMs propietarios y ejecución; pendiente de lectura crítica.
- [Proprietary AMMs and Ethereum — ethresear.ch](https://ethresear.ch/t/proprietary-amms-and-ethereum/25543) — discusión técnica sobre PropAMMs y su relación con Ethereum.

## 8. Preguntas para evaluar una integración

- [ ] ¿Qué stablecoin es: quién la emite, qué reservas declara, qué derecho de canje ofrece y qué controles de congelamiento aplican?
- [ ] ¿Cuál es el contrato oficial y cuál es el `chainId` de la red?
- [ ] ¿Qué parte del flujo ocurre on-chain y qué parte depende de exchange, custodio, banco, PSP u off-ramp?
- [ ] ¿Cómo se detectan depósitos y se evita acreditar dos veces el mismo evento?
- [ ] ¿Cuál es la política ante reorganizaciones de cadena, red o activo equivocados y transacciones fallidas?
- [ ] ¿Qué L2 o puente interviene y qué riesgos de liquidez, retiro y dependencia de terceros añade?
- [ ] ¿Está disponible para el país, tipo de cliente y moneda de salida requeridos?

## Lectura relacionada

- [Ruta DeFi: Morpho y Meteora DLMM](defi-morpho-meteora.md)
