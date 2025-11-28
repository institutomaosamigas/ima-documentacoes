---
id: doacoes
sidebar_position: 1
title: Doações (PayPal)
---

# Pagamento via PayPal

Documentação dos cenários de teste da funcionalidade de doação única e
mensal utilizando PayPal.

------------------------------------------------------------------------

## Credenciais de Teste

**Email:** sb-g6rrs47518084@personal.example.com\
**Senha:** 8,\*EF#h}

------------------------------------------------------------------------

## Ambiente de Teste

-   **Ambiente:** DevTools\
-   **Dispositivo:** Samsung Galaxy S8+\
-   **Dimensão:** 360x740px\
-   **User agent:**
    `Mozilla/5.0 (Linux; Android 12; Pixel 5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/121.0 Mobile Safari/537.36`

------------------------------------------------------------------------

## User Story

**Como** pessoa usuária no site mobile\
**Quero** realizar o pagamento via PayPal\
**Para** realizar uma doação única ou mensal

------------------------------------------------------------------------

## Background

``` gherkin
Given que eu esteja na tela de doações
And a URL é https://www.maosamigas.org/doacoes
```

------------------------------------------------------------------------

# Cenários Positivos

### Scenario 01 --- Doação única com 200 reais

**Status:** Passed

``` gherkin
When eu clico em 'Doação Única'
And clico no valor de 200 reais
And clico em 'Doar Agora'
Then sou redirecionado para a tela 'Pague com PayPal'

When eu clico em 'Log in'
Then sou redirecionado para tela com o resumo da doação

When clico em 'Realizar compra'
Then sou redirecionado para a tela de 'Doação realizada com sucesso'
```

------------------------------------------------------------------------

### Scenario 02 --- Doação única com 100 reais

**Status:** Passed

``` gherkin
When eu clico em 'Doação Única'
And clico no valor de 100 reais
And clico em 'Doar Agora'
Then sou redirecionado para a tela 'Pague com PayPal'

When eu clico em 'Log in'
Then sou redirecionado para tela com o resumo da doação

When clico em 'Realizar compra'
Then sou redirecionado para a tela de 'Doação realizada com sucesso'
```

------------------------------------------------------------------------

### Scenario 03 --- Doação única com 50 reais

**Status:** Passed

``` gherkin
When eu clico em 'Doação Única'
And clico no valor de 50 reais
And clico em 'Doar Agora'
Then sou redirecionado para a tela 'Pague com PayPal'

When eu clico em 'Log in'
Then sou redirecionado para tela com o resumo da doação

When clico em 'Realizar compra'
Then sou redirecionado para a tela de 'Doação realizada com sucesso'
```

------------------------------------------------------------------------

### Scenario 04 --- Doação única com 25 reais

**Status:** Passed

``` gherkin
When eu clico em 'Doação Única'
And clico no valor de 25 reais
And clico em 'Doar Agora'
Then sou redirecionado para a tela 'Pague com PayPal'

When eu clico em 'Log in'
Then sou redirecionado para tela com o resumo da doação

When clico em 'Realizar compra'
Then sou redirecionado para a tela de 'Doação realizada com sucesso'
```

------------------------------------------------------------------------

### Scenario 05 --- Doação única com 10 reais

**Status:** Passed

``` gherkin
When eu clico em 'Doação Única'
And clico no valor de 10 reais
And clico em 'Doar Agora'
Then sou redirecionado para a tela 'Pague com PayPal'

When eu clico em 'Log in'
Then sou redirecionado para tela com o resumo da doação

When clico em 'Realizar compra'
Then sou redirecionado para a tela de 'Doação realizada com sucesso'
```

------------------------------------------------------------------------

### Scenario 06 --- Doação mensal (Plano Semente)

**Status:** Passed

``` gherkin
When clico em 'Doação Mensal'
And escolho o plano 'Semente'
And clico em 'Fazer Doação'
Then sou redirecionado para a tela 'Concordar e assinar'

When eu clico no botão 'Concordar e assinar'
Then meu registro de doação mensal é realizado com sucesso
```

------------------------------------------------------------------------

### Scenario 07 --- Doação mensal (Plano Crescimento)

**Status:** Blocked

``` gherkin
When clico em 'Doação Mensal'
And escolho o plano 'Crescimento'
And clico em 'Fazer Doação'
Then sou redirecionado para a tela 'Concordar e assinar'

When eu clico no botão 'Concordar e assinar'
Then meu registro de doação mensal é realizado com sucesso
```

------------------------------------------------------------------------

### Scenario 08 --- Doação mensal (Plano Transformação)

**Status:** Blocked

``` gherkin
When clico em 'Doação Mensal'
And escolho o plano 'Transformação'
And clico em 'Fazer Doação'
Then sou redirecionado para a tela 'Concordar e assinar'

When eu clico no botão 'Concordar e assinar'
Then meu registro de doação mensal é realizado com sucesso
```

------------------------------------------------------------------------

### Scenario 09 --- Cancelamento de pagamento

**Status:** Passed

``` gherkin
When clico em 'Doação Mensal'
And escolho o plano 'Semente'
And clico em 'Fazer Doação'
Then sou redirecionado para a tela 'Concordar e assinar'

When eu clico em 'Cancelar e voltar para Instituto IMA'
Then a seguinte mensagem é exibida 'Doação Cancelada'
```

------------------------------------------------------------------------

### Scenario 10 --- Inserção de valor alto

**Status:** Passed

``` gherkin
When eu clico em 'Doação Única'
And preencho o campo 'Ou insira outro valor (R$)' com '300.000,00'
And o sistema exibir como disponível o botão 'Fazer Doação'
Then devo realizar a doação
```

------------------------------------------------------------------------

### Scenario 11 --- Inserção de valor com vírgula

**Status:** Passed

``` gherkin
When eu clico em 'Doação Única'
And preencho o campo 'Ou insira outro valor (R$)' com '3,2345'
And o sistema exibir como disponível o botão 'Fazer Doação'
Then devo realizar a doação
```

------------------------------------------------------------------------

### Scenario 12 --- Doação via Pix

**Status:** Failed (botão copiar não responsivo)

``` gherkin
When eu clico em 'Pix'
And clico em copiar a chave pix
Then a chave pix é copiada para a área de transferência
```

------------------------------------------------------------------------

# Cenário Negativo

### Scenario 13 --- Inserção de valor inválido

**Status:** Failed → Retested → Passed

``` gherkin
When eu clico em 'Doação Única'
And preencho o campo 'Ou insira outro valor (R$)' com valor menor que R$1,00
Then o sistema não deve permitir habilitar o botão 'Fazer Doação'
```

> Resultado anterior: o botão 'Fazer Doação' ficava disponível com valor
> menor que R\$1,00.\
> Resultado atual: **Passou**.

------------------------------------------------------------------------

# Teste de Carga

### Scenario 14 --- Teste de carga com 30 usuários

**Status:** Passed

``` gherkin
When 30 usuários acessam simultaneamente o app no fluxo de doações
Then o tempo médio de resposta deve ser inferior a 1000ms
And a taxa de erro deve ser inferior a 1%
```

------------------------------------------------------------------------
