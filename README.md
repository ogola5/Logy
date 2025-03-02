## Logy
![Add_blog_post](https://i.ibb.co/28VrHph/Screenshot-from-2023-11-24-19-22-57.png)

# Description
 A simplified example of a Rust code for an Internet Computer (ICP) canister to manage blog posts, including a function to tip the creator or writer.

 ## Technologies Used
 - Rust

![delete_blog_post](https://i.ibb.co/6NMqLpf/Screenshot-from-2023-11-24-19-46-59.png)
![get_blog_post](https://i.ibb.co/w0y0PmZ/Screenshot-from-2023-11-24-19-46-08.png)
![Tip_blog_post](https://i.ibb.co/yh0q10j/Screenshot-from-2023-11-24-19-25-15.png)
![Update](https://i.ibb.co/j4QwX09/Screenshot-from-2023-11-24-19-27-42.png)

## How it works!

1. **Add a post**
![Add_blog_post](https://i.ibb.co/28VrHph/Screenshot-from-2023-11-24-19-22-57.png)

2. **Get blog post**
![get_blog_post](https://i.ibb.co/w0y0PmZ/Screenshot-from-2023-11-24-19-46-08.png)

3. **Update Post**
![Update](https://i.ibb.co/j4QwX09/Screenshot-from-2023-11-24-19-27-42.png)

4. **Tip blog post**
![Tip_blog_post](https://i.ibb.co/yh0q10j/Screenshot-from-2023-11-24-19-25-15.png)

5. **Delete blog post**
![delete_blog_post](https://i.ibb.co/6NMqLpf/Screenshot-from-2023-11-24-19-46-59.png)

## icp_Logy_contract

### Requirements
* rustc 1.64 or higher
```bash
$ curl --proto '=https' --tlsv1.2 https://sh.rustup.rs -sSf | sh
$ source "$HOME/.cargo/env"
```
* rust wasm32-unknown-unknown target
```bash
$ rustup target add wasm32-unknown-unknown
```
* candid-extractor
```bash
$ cargo install candid-extractor
```
* install `dfx`
```bash
$ DFX_VERSION=0.15.0 sh -ci "$(curl -fsSL https://sdk.dfinity.org/install.sh)"
$ echo 'export PATH="$PATH:$HOME/bin"' >> "$HOME/.bashrc"
$ source ~/.bashrc
$ dfx start --background
```

If you want to start working on your project right away, you might want to try the following commands:

```bash
$ cd icp_rust_boilerplate/
$ dfx help
$ dfx canister --help
```

## Update dependencies

update the `dependencies` block in `/src/{canister_name}/Cargo.toml`:
```
[dependencies]
candid = "0.9.9"
ic-cdk = "0.11.1"
serde = { version = "1", features = ["derive"] }
serde_json = "1.0"
ic-stable-structures = { git = "https://github.com/lwshang/stable-structures.git", branch = "lwshang/update_cdk"}
```

## did autogenerate

Add this script to the root directory of the project:
```
https://github.com/buildwithjuno/juno/blob/main/scripts/did.sh
```

Update line 16 with the name of your canister:
```
https://github.com/buildwithjuno/juno/blob/main/scripts/did.sh#L16
```

After this run this script to generate Candid.
Important note!

You should run this script each time you modify/add/remove exported functions of the canister.
Otherwise, you'll have to modify the candid file manually.

Also, you can add package json with this content:
```
{
    "scripts": {
        "generate": "./did.sh && dfx generate",
        "gen-deploy": "./did.sh && dfx generate && dfx deploy -y"
      }
}
```

and use commands `npm run generate` to generate candid or `npm run gen-deploy` to generate candid and to deploy a canister.

## Running the project locally

If you want to test your project locally, you can use the following commands:

```bash
# Starts the replica, running in the background
$ dfx start --background

# Deploys your canisters to the replica and generates your candid interface
$ dfx deploy
```
