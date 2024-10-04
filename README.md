let bjs = require('bitcoinjs-lib')

let input = Buffer.from('3afeef2137311d2cbab6b393df30d1961565601c4967a29725b3989527aa4d4b', 'hex')
let witness = [
  Buffer.from('3afeef2137311d2cbab6b393df30d1961565601c4967a29725b3989527aa4d4b', 'hex'),
  Buffer.from('035c618df829af694cb99e664ce1b34f80ad2c3b49bcd0d9c0b1836c66b2d25fd8', 'hex')
]

let p2sh = bjs.payments.p2sh({ input, witness })
console.log(p2sh.address)
// bc1qwj7k0zvvxsrhf4x2z3frar5gp6et24anksdqjj

let redeem = bjs.payments.p2wpkh(p2sh.redeem)
console.log(redeem.address)
bc1qwj7k0zvvxsrhf4x2z3frar5gp6et24anksdqjj