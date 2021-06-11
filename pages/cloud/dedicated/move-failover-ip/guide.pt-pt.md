---
title:  Migrar um IP Failover
excerpt: Saiba como migrar um IP Failover a partir da Área de Cliente ou através das API OVHcloud
slug: ip-fo-move
section: Redes & IP
order: 7
---

**Última atualização: 12/03/2021**

## Objetivo

Os IP Failover podem ser migrados entre os serviços que utiliza. O interesse é não perder a sua reputação, o seu referenciamento e melhorar a continuidade do serviço das suas aplicações e sistemas.
Esta tecnologia permite-lhe trocar os endereços IP de uma solução para outra em menos de um minuto, praticamente sem qualquer interrupção para os seus utilizadores. Pode ser utilizada durante as migrações de serviços (deslocação dos projetos do ambiente de desenvolvimento para o de produção, por exemplo) ou aquando da migração para um servidor de recurso em caso de falha.

**Saiba como migrar um IP Failover a partir da Área de Cliente OVHcloud ou através das API OVHcloud**

## Requisitos

- Ter um [servidor dedicado](https://www.ovhcloud.com/pt/bare-metal/){.external} na Área de Cliente OVHcloud.
- Dispor de um [endereço IP Failover](https://www.ovhcloud.com/pt/bare-metal/ip/).
- Ter acesso à [Área de Cliente OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.pt/&ovhSubsidiary=pt){.external}.

## Instruções

> [!primary]
> Um IP Fail Over não pode ser migrado de uma zona para outra. Por exemplo, um IP situado no datacenter SBG poderá ser migrado para GRA ou RBX mas não poderá ser migrado para BHS

### Migrar um IP a partir da Área de Cliente OVHcloud

Aceda à [Área de Cliente OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.pt/&ovhSubsidiary=pt), clique no menu `Bare Metal Cloud`{.action} e, a seguir, na secção `IP`{.action} no final da coluna, à esquerda da página.

![Área de Cliente](images/manager01.png){.thumbnail}

O menu pendente "Service" permite-lhe selecionar apenas os endereços IP Failover.

Clique no botão `...`{.action} à direita do endereço IP a migrar e, a seguir, em `Migrar o IP failover`{.action}.

![Área de Cliente](images/manager02.png){.thumbnail}

No menu contextual que aparece, selecione o serviço para o qual mover o endereço IP.

Clique em `Seguinte`{.action} e depois em `Validar`{.action}.

![Área de Cliente](images/manager03.png){.thumbnail}

### Migrar um IP através das API

Aceda à página web das [API OVHcloud](https://api.ovh.com/).

Numa primeira fase, é preferível verificar se o endereço IP pode ser migrado.
<br>Para verificar se o IP pode ser migrado para um dos seus servidores dedicados, utilize a seguinte chamada:

> [!api]
>
> @api {GET} /dedicated/server/{serviceName}/ipCanBeMovedTo
>

- `serviceName`: a referência do servidor dedicado de destino
- `ip`: o endereço IP Fail Over a migrar

Para migrar o endereço IP, utilize a seguinte chamada:

> [!api]
>
> @api {POST} /dedicated/server/{serviceName}/ipMove
>

- `serviceName`: a referência do servidor dedicado de destino
- `ip`: o endereço IP Fail Over a migrar

## Saiba mais

Fale com a nossa comunidade de utilizadores em <https://community.ovh.com/en/>.
