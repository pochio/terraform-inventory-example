
# terraform-inventory-example

以下のことを試したので、メモを残しとく

- Terraform を利用して VMware vCenter でVMのクローン
  - ホスト名、IPアドレスなどの初期設定
- terraform-inventory と利用して、Ansible と連携
  - ミドルウェアの導入と設定

## Terraform の実行

```bash
vi variables.tf
terraform init
terrafrom plan
terraform apply
```

## Ansible の実行

- ```su``` とかしてるのはテスト環境の問題
- ```terraform-inventory``` のコマンドはフルパスで指定しないとダメだった

```bash
ansible-playbook \
    --ask-pass \
    --ask-su-pass \
    --become-method=su \
    --inventory-file=~/bin/terraform-inventory \
    apache-playbook.yaml
```
