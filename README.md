const tx = JSON.parse(apiResponseAbove)

let inputAddresses = []
let inputs = tx.transaction.inputs

inputs.forEach(input => {

  let scriptSigChunks = input.script_sig.asm.split(/\s+/)
  if (scriptSigChunks[0] === '') scriptSigChunks = []

  if(input.witness === null) {
    console.log('not segwit')
    return
  } else if(scriptSigChunks.length > 1) {
    console.log('unknown input type: scriptSig is not P2SH but has witness')
    return
  } else if(scriptSigChunks.length === 0) {

    // is not P2SH
    let witnessScript = input.witness[input.witness.length - 1]
    let witnessType
    let pubKey
    if (witnessScript.match(/^0[23][0-9a-fA-F]{64}$/)) {
      pubKey = witnessScript
      witnessType = 'P2WPKH'
    } else {
      witnessType = 'P2WSH'
    }

    // get address from the hash160 of pubKey OR the sha256 of witnessScript depending on P2WPKH or P2WSH respectively

  } else {

    // is P2SH
    let redeemScript = scriptSigChunks[0]
    let witnessScript = input.witness[input.witness.length - 1]
    let witnessType
    if (witnessScript.match(/^0[23][0-9a-fA-F]{64}$/)) {
      witnessType = 'P2SH-P2WPKH'
    } else {
      witnessType = 'P2SH-P2WSH'
    }

    // get address from redeemScript hash160
  }

})