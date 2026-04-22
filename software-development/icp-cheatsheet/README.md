# ICP CHEATSHEET

> ## DFX CLI Commands

```bash
# Installation
curl -fsSL https://internetcomputer.org/install.sh | sh
source $HOME/.local/share/dfx/env

# Local Develop

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# ICP Quick Reference - The Great Cryptonio's Cheatsheet

## DFX CLI Commands

```bash
# Installation
curl -fsSL https://internetcomputer.org/install.sh | sh
source $HOME/.local/share/dfx/env

# Local Development
dfx start --background              # Start local IC replica
dfx stop                            # Stop replica
dfx restart                         # Restart replica
dfx start --clean                   # Clean start (removes state)

# Project Management
dfx new my_project --type motoko   # Create new Motoko project
dfx new my_project --type rust     # Create new Rust project
dfx build                          # Build all canisters
dfx deploy                         # Deploy locally
dfx deploy --network ic            # Deploy to mainnet

# Canister Operations
dfx canister call CANISTER_NAME METHOD '(ARGUMENTS)'
dfx canister id CANISTER_NAME      # Get canister ID
dfx canister status CANISTER_NAME --network ic
dfx canister delete CANISTER_NAME --network ic

# Identity Management
dfx identity get-principal         # Get your principal
dfx identity new NAME              # Create new identity
dfx identity use NAME              # Switch identity

# Cycles (Mainnet)
dfx cycles balance --network ic
dfx cycles convert --amount 5.0 --network ic
dfx canister --network ic deposit-cycles AMOUNT CANISTER_NAME
```

## Motoko Types

```motoko
// Primitives
let n : Nat = 1;                   // Natural number (0, 1, 2...)
let i : Int = -1;                  // Integer (...-1, 0, 1...)
let t : Text = "hello";            // String
let b : Bool = true;               // Boolean
let p : Principal = ...;            // Principal ID

// Collections
let arr : [Nat] = [1, 2, 3];       // Array
let list : List.List<T>;           // Linked list
let map : HashMap.HashMap<K, V>;   // Hash map

// Options & Results
let some : ?Nat = ?42;             // Some value
let none : ?Nat = null;            // No value
let ok : Result<T, E> = #ok val;   // Success
let err : Result<T, E> = #err e;   

*[truncated — see source for full prompt]*