# Laboratório Prático 6 – Publicando o Primeiro Site da Empresa
**Professor:** Cefras Mandú
**Aluno:** *Hugo de Lima Santos*

---

## Objetivo

Instalar e configurar um servidor Web (**Apache2**) e um servidor DNS (**BIND9**) em uma máquina virtual Ubuntu Server, permitindo o acesso a uma página web tanto pelo **endereço IP** quanto por um **nome de domínio local** (`empresa.local`).

---

## Ambiente Utilizado

* Sistema Operacional: Ubuntu Server
* Virtualização: Oracle VirtualBox
* IP da VM: `10.0.2.15` (ou o IP configurado na sua VM)

---

## Etapa 1 – Instalação e Configuração do Apache

O Apache foi instalado e configurado para exibir uma página HTML personalizada.

**Resultado esperado:** acesso via navegador ao IP da VM exibindo a mensagem de boas-vindas.

📸 **Print:** Página web acessível via `http://IP_DA_VM`
<img width="1222" height="443" alt="Screenshot from 2026-01-22 03-09-05" src="https://github.com/user-attachments/assets/b1d7894c-9f25-48a7-ac16-8c0f95b15d70" />



## Etapa 2 – Instalação e Configuração do BIND9

O serviço BIND9 foi instalado e configurado como servidor DNS autoritativo para o domínio local `empresa.local`.

### Configurações realizadas:

* Criação da zona `empresa.local` no arquivo `named.conf.local`
* Criação do arquivo de zona direta `db.empresa.local`

📸 **Print:** Conteúdo do arquivo `/etc/bind/named.conf.local`
<img width="840" height="406" alt="Screenshot from 2026-01-22 03-10-02" src="https://github.com/user-attachments/assets/c884e290-912d-4654-a202-848c62d07329" />

📸 **Print:** Conteúdo do arquivo `/etc/bind/db.empresa.local`
<img width="840" height="406" alt="Screenshot from 2026-01-22 03-10-43" src="https://github.com/user-attachments/assets/1ec49819-69d6-4de4-8ff0-bb897c8f6209" />

---

## Etapa 3 – Reinício dos Serviços e Configuração do Cliente DNS

Após a configuração, o serviço BIND9 foi reiniciado e o sistema configurado para utilizar o DNS local (`127.0.0.1`).

📸 **Print:** Status do serviço BIND9 (`active (running)`)
<img width="1177" height="526" alt="Screenshot from 2026-01-22 03-11-44" src="https://github.com/user-attachments/assets/128599a7-e253-4714-9afb-bc5f0786e9a9" />

📸 **Print:** Configuração do DNS local (`/etc/resolv.conf` ou `resolvectl status`)

<img width="1226" height="691" alt="Screenshot from 2026-01-22 03-12-52" src="https://github.com/user-attachments/assets/2ad70316-2d62-41c0-8838-d1c33ef52379" />


## Testes de Funcionamento

### Teste de Resolução de Nome (DNS)

O domínio `www.empresa.local` foi resolvido corretamente para o IP da máquina virtual.

📸 **Print:** Comando `dig www.empresa.local` mostrando a resposta correta
<img width="1226" height="691" alt="Screenshot from 2026-01-22 03-13-38" src="https://github.com/user-attachments/assets/883504fb-7a9c-4202-a1e2-15f67503933d" />

---

### Teste Final com Curl

O acesso ao site pelo nome de domínio foi testado com sucesso via linha de comando.

📸 **Print:** Comando `curl http://www.empresa.local` exibindo a mensagem HTML
<img width="1219" height="258" alt="Screenshot from 2026-01-22 03-14-25" src="https://github.com/user-attachments/assets/a5b44e8c-91ef-43ec-aab9-686bd85442b5" />

---

## Conclusão

Todos os objetivos do laboratório foram alcançados com sucesso. O servidor Apache está funcionando corretamente, o BIND9 resolve o domínio `empresa.local`, e o acesso à página web ocorre tanto via IP quanto via nome de domínio, conforme solicitado no enunciado da prática.

---

📁 **Observação:** Os prints comprobatórios de cada etapa estão disponíveis na pasta `prints/` do repositório.
