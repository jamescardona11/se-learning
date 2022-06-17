# web3

Cosas importantes:

- function <name> public/internal
- memory par strings
- **using** y **library** es similar a (extensiones en flutter)
- [**modifier**][modifier] es para cambiar el comportamiento de una función
- receive: función que se llama cuando llaman el contrato sin data
- fallback: se llama con data pero no hace match con alguna función en el contrato

// Explainer from: https://solidity-by-example.org/fallback/
// Ether is sent to contract
// is msg.data empty?
// / \
// yes no
// / \
// receive()? fallback()
// / \
// yes no
// / \
//receive() fallback()
