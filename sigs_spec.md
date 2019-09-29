## ARCHIVED and outdated - do not use.

These are temp params for the MVP1 testnet milestone and are likely to change before mainnet.

# BLS signature

	e : G1 x G2 -> Fp12
	Q in G2 ; fixed global parameter
	H : {str} -> G1
	s : secret key
	sQ ; public key
	s H(m) ; signature of m
	verify ; e(sQ, H(m)) = e(Q, s H(m))
  
- Curve name:: BLS12_381
- Public key size: 288 bytes
- Private key size: 48 bytes

# Key Deriviation
12 words mnemonic -> 128 bits random seed -> sha-512(seed) = 64 seed bytes
- 48 bytes to to first private key
- 16 bytes - kept as chain code - used for key deriviation

# Derived key i (for depth 0 only):
- priv-k(i) = hmac-sha512(priv-key-parent, i, chain-code, const-salt)
- We only derive private keys as public key can be derived from private

# Curve params
Curve: 52435875175126190479447740508185965837690552500527637822603658699938581184513
Field: 4002409555221667393417789825735904156556882819939007885332058136124031650490837864442687629129015664037894272559787

q: 0x1a0111ea397fe69a4b1ba7b6434bacd764774b84f38512bf6730d2a0f6b0f6241eabfffeb153ffffb9feffffffffaaab
r: 0x73eda753299d7d483339d80809a1d80553bda402fffe5bfeffffffff00000001

G2.aa: 0x024aa2b2f08f0a91260805272dc51051c6e47ad4fa403b02b4510b647ae3d1770bac0326a805bbefd48056c8c121bdb8
G2.ab: 0x13e02b6052719f607dacd3a088274f65596bd0d09920b61ab5da61bbdc7f5049334cf11213945d57e5ac7d055d042b7e
G2.ba: 0x0ce5d527727d6e118cc9cdc6da2e351aadfd9baa8cbdd3a76d429a695160d12c923ac9cc3baca289e193548608b82801
G2.bb: 0x0606c4a02ea734cc32acd2b02bc28b99cb3e287e85a763af267492ab572e99ab3f370d275cec1da1aaa9075ff05f79be

G1.a: 0x17f1d3a73197d7942695638c4fa9ac0fc3688c4f9774b905a14e3a3f171bac586c55e83ff97a1aeffb3af00adb22c6bb
G1.b: 0x08b3f481e3aaa0f1a09e30ed741d8ae4fcf5e095d5d00af600db18cb2c04b3edd03cc744a2888ae40caa232946c5e7e1
