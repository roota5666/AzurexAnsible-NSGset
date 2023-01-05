# AzurexAnsible-NSGset

## Features

AzureのNSGをAnsibleで作成します。  
このリポジトリは、Zennの記事 [Azure設定をAnsibleで実行する～NSG設定編～](https://zenn.dev/roota5666/articles/202212-06t-azurexansible-nsg)で使用するために作成したリポジトリです。

## Environment

- azure-cli: 2.43.0
- ansible: core 2.13.3

## Usage

### Run

- git clone
  ```bash
  git clone https://github.com/roota5666/AzurexAnsible-NSGset
  cd AzurexAnsible-NSGset
  ```
- 環境に合わせて1. または 2. の対応を実施
  1. AzureCLIで下記を実行してResourceGroup「example」を作成する
     ```bash
     az group create --location japaneast --name example
     ```
  1. ResourceGroup名をご自分の環境に合わせてimportファイル内の「example」を置換する
     ```bash
     vi import.json
     ```
- dry-run
  ```bash
  ansible-playbook run.yml --extra-vars "importjson=./import.json" --check
  ```
- run
  ```bash
  ansible-playbook run.yml --extra-vars "importjson=./import.json"
  ```

### Directory Tree

```text
/
|-- import.json
|-- README.md
|-- run.yml
`-- roles/az_securitygroup/tasks
    `-- main.yml
```

## Reference Document

- [azure_rm_securitygroup](https://docs.ansible.com/ansible/latest/collections/azure/azcollection/azure_rm_securitygroup_module.html)
- galaxy [az_securitygroup](https://galaxy.ansible.com/jesperberth/az_securitygroup)
- github [az_securitygroup](https://github.com/jesperberth/az_securitygroup)

## LICENSE

[MIT](./LICENSE)

## Author

[roota5666](https://github.com/roota5666)
