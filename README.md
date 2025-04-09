# lighthouse


## Local setup
sudo apt install curl
curl https://sh.rustup.rs -sSf | sh
source $HOME/.cargo/env
curl https://rustwasm.github.io/wasm-pack/installer/init.sh -sSf | sh


## Local build
cargo build
cargo run

## Internet build
rustup target add wasm32-unknown-unknown
cargo install wasm-bindgen-cli
cargo build --release --target wasm32-unknown-unknown
wasm-bindgen target/wasm32-unknown-unknown/release/lighthouse.wasm \
  --out-dir web/pkg \
  --target web
cd web
python3 -m http.server
http://localhost:8000
 

 