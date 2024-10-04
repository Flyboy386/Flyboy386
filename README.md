let bjs = require('bitcoinjs-lib')

let input = Buffer.from('160014e5e6cc9c155da3c9df725c3c4d9987c374e29987', 'hex')
let witness = [
  Buffer.from('30450221009f696a5c1bb1735bb3f1f64276ac6838c4e04b6c89b5eda84e86d24022d4f7ab02207caae352a19fe830dea60be2cd0a73af27e40124ca7f57ff9451887e81a7569d01', 'hex'),
  Buffer.from('035c618df829af694cb99e664ce1b34f80ad2c3b49bcd0d9c0b1836c66b2d25fd8', 'hex')
]

let p2sh = bjs.payments.p2sh({ input, witness })
console.log(p2sh.address)
// bc1qwj7k0zvvxsrhf4x2z3frar5gp6et24anksdqjj

let redeem = bjs.payments.p2wpkh(p2sh.redeem)
console.log(redeem.address)
bc1qwj7k0zvvxsrhf4x2z3frar5gp6et24anksdqjj