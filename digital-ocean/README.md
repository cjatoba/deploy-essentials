# Configuração para acesso SSH

## Primeiro acesso
```bash
ssh root@ip_do_droplet
```

## Criar usuário (não root)
```bash
adduser new-user-name
```

## Adicionar o novo usuário no grupo sudo
```bash
usermod -aG sudo new-user-name
```

## Habilitar acesso ssh para o novo usuário
```bash
cd ~
mkdir .ssh
cd .ssh/
sudo cp /root/.ssh/authorized_keys .
sudo chown new-user-name:new-user-name authorized_keys
```

## Remover a permissão de acesso com o usuário root

- (Alerta) Antes de iniciar o processo conferir se o acesso com o novo usuário (configurado no passo anterior) está funcionando;

- Abrir o arquivo de configuração do SSH: 
```bash
sudo vim /etc/ssh/sshd_config
```

- Alterar a linha `PermitRootLogin yes` para `PermitRootLogin no`

- Reiniciar o serviço do SSH
```bash
sudo service ssh restart
```

# Configuração do firewall

- Acessar o projeto na DigitalOcean;
- Acessar o droplet;
- Selecionar a opção `Networking`;
- Na seção `Firewalls` selecionar a opção `Edit`;
- Clicar no botão `Create Firewall`;
- Na seção `Name`atribuir um nome a nova regra;
- Na seção `Inbound Rules` selecionar a opção `New role` e selecionar `HTTP`;
- Na seção `Inbound Rules` selecionar a opção `New role` e selecionar `HTTPS`;
- Na seção `Apply to 



lets` informar o nome do droplet em que a regra será aplicada ou `All Droplets` para aplicar a regra em todos so droplets;
- Clicar no botão `Create Firewall`;
