Here is the **finalized README** for **DogecoinEV Ordinals Indexer**, with **inscription height set to 0** and **RPC port set to 42069**:

---

```markdown
# DogecoinEV Ordinals Indexer MAY STILL HAVE BUGS

ℹ️ This is a fork adapted for the DogecoinEV blockchain from [apezord/ord-dogecoin](https://github.com/apezord/ord-dogecoin).

## **Prerequisites**
To run the **DogecoinEV Ordinals Indexer**, you must set up and fully sync a **DogecoinEV** node.

### 1. Install DogecoinEV Core  
Download and install the latest version from [DogecoinEV Core](https://github.com/DogecoinEV-Foundation/DogecoinEV).

### 2. Start Your DogecoinEV Node  
Run the following command to start **DogecoinEV Core** with the required flags:

```shell
dogecoinevd -txindex -rpcuser=your_username -rpcpassword=your_password -rpcport=42069 -rpcallowip=0.0.0.0/0 -rpcbind=127.0.0.1
```

- Ensure your **DogecoinEV node is fully synced** before starting the indexer.
- ‼️ **IMPORTANT**: Replace `your_username` and `your_password` with secure credentials.

---

## **Building the Indexer**

### 1. Install Dependencies  
Ensure that you have the necessary dependencies installed:

```shell
sudo apt update && sudo apt install -y build-essential clang pkg-config libssl-dev git
```

### 2. Install Rust  
If you don't have **Rust** installed, install it using the following command:

```shell
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source $HOME/.cargo/env
```

### 3. Clone the Repository  
```shell
git clone https://github.com/DogecoinEV-Foundation/ord-dogecoinev.git
cd ord-dogecoinev
```

### 4. Build the Release Version  
```shell
cargo build --release
```

---

## **Running the Indexer**

### **1. Ensure the Data Directory Exists**
```shell
mkdir -p /mnt/ord-node/indexer-data-main
```

### **2. Start Indexing**
Replace `YOUR_RPC_URL` with your actual **DogecoinEV node URL** (e.g., `http://your_username:your_password@127.0.0.1:42069`).

```shell
./target/release/ord \
    --first-inscription-height=0 \
    --rpc-url=http://your_username:your_password@127.0.0.1:42069 \
    --data-dir=/mnt/ord-node/indexer-data-main \
    --index-transactions \
    --index-dunes \
    --index-drc20 \
    --nr-parallel-requests=16 \
    index
```

### **3. Start the Indexer with the Server**
```shell
./target/release/ord \
    --first-inscription-height=0 \
    --rpc-url=http://your_username:your_password@127.0.0.1:42069 \
    --data-dir=/mnt/ord-node/indexer-data-main \
    --index-transactions \
    --index-dunes \
    --index-drc20 \
    --nr-parallel-requests=16 \
    server --http-port 8080
```

---

## **Important Parameters**
- `--index-transactions`: Stores transaction data for better API performance.
- `--index-drc20`: Enables indexing of **DRC-20 tokens, including Dev-20’s** *(subject to change)*.
- `--index-dunes`: Enables indexing of **Dunes**.
- `--nr-parallel-requests=16`: Configures parallel requests to your RPC Server.
- `--data-dir`: Specifies where the indexer stores its data.
- `--http-port`: The port where the server will listen (**default: 8080**).

---

## **Storage Requirements**
The database size depends on the indexing options enabled and the current blockchain size. Ensure you have at least **400GB of free storage**.

---

## **API Documentation**
You can find the API documentation in the [openapi.yaml](https://github.com/DogecoinEV-Foundation/ord-dogecoinev/blob/main/openapi.yaml) file.  
The most convenient way to view the API documentation is to use the [Swagger Editor](https://editor.swagger.io/).

---

## **Troubleshooting**

### **Indexer Not Syncing?**
- Ensure that **DogecoinEV Core** is running and fully synced.
- Confirm that `-txindex` is enabled in your **DogecoinEV** node.
- Check that `rpcuser` and `rpcpassword` match in both `dogecoinevd` and the indexer command.

### **Out of Disk Space?**
- You need at least **400GB** of free space for the full index.

### **Indexer Crashing?**
- Run the command with `RUST_BACKTRACE=1` for more debugging information:
  ```shell
  RUST_BACKTRACE=1 ./target/release/ord --rpc-url=http://your_username:your_password@127.0.0.1:42069 --data-dir=/mnt/ord-node/indexer-data-main index
  ```

---

## **Contributing**
Contributions are welcome! Please feel free to submit a **Pull Request**.  
For major changes, open an **Issue** first to discuss the modifications.

---

## **License**
This project is licensed under [CC0-1.0 license](https://github.com/DogecoinEV-Foundation/ord-dogecoinev/blob/main/LICENSE).

---

## **Repository**
For more information, source code, and updates, visit the [GitHub repository](https://github.com/DogecoinEV-Foundation/ord-dogecoinev).
```

