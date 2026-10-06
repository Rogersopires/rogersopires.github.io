# Sistema Financeiro

Sistema financeiro pessoal usando **Markdown/texto como fonte de dados** e **HTML como interface**.

---

## 1. Lançamento

Formato:

```text id="e0a9m8"
DATA | VALOR | DESCRIÇÃO | CATEGORIA > SUBCATEGORIA | PARÂMETROS
```

Exemplo:

```text id="1w0v7s"
2026-10-05 | -150.00 | Mercado | Alimentação > Mercado | conta=NuBank
```

Outro exemplo:

```text id="q5v7kc"
2026-10-05 | 8000.00 | Salário | Receitas > Salário | conta=Itaú
```

---

## 2. Tipos

Tipos disponíveis:

```text id="yq7m2d"
receita | despesa | transferencia | investimento | resgate | rendimento | dividendo | juros | taxa | amortizacao | estorno | financiamento | emprestimo
```

Exemplos:

```text id="j4s1w8"
2026-10-05 | 8000 | Salário | Receitas > Salário | tipo=receita
2026-10-06 | -150 | Mercado | Alimentação > Mercado | tipo=despesa
2026-10-07 | -500 | Transferência | Transferência > Entre contas | tipo=transferencia
2026-10-08 | -1000 | Aporte | Investimentos > FIIs | tipo=investimento
2026-10-15 | 1100 | Resgate | Investimentos > FIIs | tipo=resgate
2026-10-20 | 50 | Rendimento | Investimentos > Renda Fixa | tipo=rendimento
2026-10-25 | 30 | Dividendo | Investimentos > FIIs | tipo=dividendo
2026-10-25 | 20 | Juros | Investimentos > Renda Fixa | tipo=juros
2026-10-26 | -10 | Taxa | Investimentos > Renda Fixa | tipo=taxa
2026-10-27 | -500 | Amortização | Moradia > Financiamento | tipo=amortizacao
2026-10-28 | 100 | Estorno | Receitas > Outros | tipo=estorno
2026-10-30 | -1200 | Parcela | Moradia > Financiamento | tipo=financiamento
2026-10-31 | -800 | Empréstimo | Dívidas > Empréstimos | tipo=emprestimo
```

---

## 3. Valores

Valores positivos representam entrada e negativos representam saída.

```text id="j5p9bx"
2026-10-05 | 8000 | Salário | Receitas > Salário | tipo=receita
2026-10-05 | -150 | Mercado | Alimentação > Mercado | tipo=despesa
```

---

## 4. Categorias e subcategorias

Formato:

```text id="u8d3pw"
Categoria > Subcategoria
```

Categorias:

```text id="1q4yvx"
Alimentação | Moradia | Transporte | Saúde | Lazer | Educação | Eletrônicos | Vestuário | Investimentos | Receitas | Dívidas
```

Exemplos:

```text id="2j9k7c"
Alimentação > Mercado
Alimentação > Restaurante
Moradia > Energia
Moradia > Aluguel
Transporte > Combustível
Saúde > Medicamentos
Lazer > Jogos
Educação > Cursos
Eletrônicos > Computador
Vestuário > Roupas
Investimentos > FIIs
Receitas > Salário
Dívidas > Empréstimos
```

---

## 5. Contas

Uma conta representa onde o dinheiro está.

Tipos:

```text id="3z6m1k"
conta | dinheiro | investimento
```

Exemplos:

```text id="7p3f8x"
NuBank | tipo=conta
Itaú | tipo=conta
Carteira | tipo=dinheiro
XP | tipo=investimento
```

Lançamento associado:

```text id="9w2n5q"
2026-10-05 | -150 | Mercado | Alimentação > Mercado | conta=NuBank
```

---

## 6. Transferências

Transferências movimentam dinheiro entre contas, mas não são receita nem despesa.

Exemplo:

```text id="4k7s2m"
2026-10-07 | -500 | Transferência | Transferência > Entre contas | tipo=transferencia conta=NuBank destino=Itaú
```

Resultado:

```text id="n8x1cd"
NuBank: -500
Itaú: +500
```

---

## 7. Cartões

Cartão possui limite, fechamento e vencimento.

Exemplo:

```text id="6r3v9p"
NuBank | limite=5000 fechamento=20 vencimento=27
```

Compra à vista:

```text id="f5q8zt"
2026-10-08 | -300 | Monitor | Eletrônicos > Computador | cartao=NuBank
```

Compra parcelada:

```text id="m2c7xa"
2026-10-08 | -3000 | Monitor | Eletrônicos > Computador | cartao=NuBank parcelas=10
```

---

## 8. Parcelas

Uma compra pode ser dividida em várias parcelas.

Exemplo:

```text id="v6t2kp"
2026-10-08 | -3000 | Monitor | Eletrônicos > Computador | cartao=NuBank parcelas=10
```

O sistema projeta:

```text id="b8w4qm"
parcela=1/10 | parcela=2/10 | parcela=3/10 | ... | parcela=10/10
```

Também pode registrar entrada e juros:

```text id="h3n9ys"
entrada=500 | juros=100
```

Exemplo completo:

```text id="p7d1kf"
2026-10-08 | -3000 | Notebook | Eletrônicos > Computador | cartao=NuBank parcelas=10 entrada=500 juros=100
```

---

## 9. Recorrências

Uma despesa pode se repetir automaticamente.

Frequências:

```text id="r9c2vx"
diaria | semanal | quinzenal | mensal | bimestral | trimestral | semestral | anual
```

Exemplo mensal:

```text id="k4m8zs"
2026-10-10 | -1200 | Aluguel | Moradia > Aluguel | recorrente=mensal
```

Exemplo anual:

```text id="t6p1wj"
2026-01-10 | -1200 | Seguro | Transporte > Seguro | recorrente=anual
```

Pode terminar em determinada data:

```text id="x9v3bn"
fim=2027-10-10
```

Ou após determinado número de ocorrências:

```text id="c5q7hm"
ocorrencias=12
```

---

## 10. Financiamentos

Financiamentos podem possuir:

```text id="e7k2rp"
valor | parcelas | juros | amortizacao | taxas | saldo_devedor
```

Exemplo:

```text id="z4m8xc"
2026-10-15 | -1238.47 | Parcela financiamento | Moradia > Financiamento | tipo=financiamento parcela=10/120 amortizacao=800 juros=400
```

Amortização extraordinária:

```text id="q6t1vb"
2026-10-20 | -5000 | Amortização extra | Moradia > Financiamento | tipo=amortizacao
```

Taxa:

```text id="w3n8kp"
2026-10-15 | -25 | Taxa financiamento | Moradia > Financiamento | tipo=taxa
```

---

## 11. Empréstimos

Empréstimos podem ser registrados como dívida ou dinheiro recebido.

Dinheiro recebido:

```text id="a8f4mz"
2026-10-01 | 5000 | Empréstimo recebido | Dívidas > Empréstimos | tipo=emprestimo
```

Pagamento:

```text id="j7c2qx"
2026-11-01 | -500 | Parcela empréstimo | Dívidas > Empréstimos | tipo=emprestimo parcela=1/10 juros=50
```

---

## 12. Investimentos

Tipos:

```text id="p3v8nm"
investimento | resgate | rendimento | dividendo | juros
```

Aporte:

```text id="d6k1xr"
2026-10-05 | -1000 | Aporte HGLG11 | Investimentos > FIIs | tipo=investimento ativo=HGLG11 quantidade=10 preco_unitario=100
```

Resgate:

```text id="s9m4yc"
2026-10-20 | 1200 | Resgate HGLG11 | Investimentos > FIIs | tipo=resgate ativo=HGLG11 quantidade=10
```

Dividendo:

```text id="v2q7hb"
2026-10-25 | 35 | Dividendo HGLG11 | Investimentos > FIIs | tipo=dividendo ativo=HGLG11
```

Rendimento:

```text id="n5x8kf"
2026-10-30 | 50 | Rendimento CDB | Investimentos > Renda Fixa | tipo=rendimento ativo=CDB
```

---

## 13. Patrimônio

Ativos:

```text id="r7m3pc"
contas | dinheiro | investimentos | imóveis | veículos | outros
```

Exemplo:

```text id="f4x9zt"
Apartamento | tipo=imovel valor=300000
```

Passivos:

```text id="k8v2bn"
financiamentos | empréstimos | dívidas | cartões
```

Exemplo:

```text id="c6q1wy"
Financiamento | tipo=financiamento saldo=120000
```

Cálculo:

```text id="m9d4sx"
Patrimônio líquido = Ativos - Passivos
```

---

## 14. Datas

O sistema identifica automaticamente:

```text id="u2k7qp"
passado | presente | futuro
```

Exemplos:

```text id="b5n8cx"
2026-10-01 | -100 | Conta paga | Moradia > Energia
2026-10-06 | -50 | Compra hoje | Alimentação > Mercado
2026-10-20 | -1200 | Aluguel | Moradia > Aluguel
```

---

## 15. Status

Status:

```text id="x4p9mv"
previsto | confirmado | cancelado
```

Exemplos:

```text id="q7n2kc"
2026-10-10 | -1200 | Aluguel | Moradia > Aluguel | status=previsto
2026-10-05 | -150 | Mercado | Alimentação > Mercado | status=confirmado
2026-10-15 | -300 | Compra cancelada | Eletrônicos > Computador | status=cancelado
```

---

## 16. Parâmetros

Os parâmetros são `chave=valor` e ficam depois da última `|`.

Exemplo:

```text id="h8m3rx"
2026-10-05 | -150 | Mercado | Alimentação > Mercado | conta=NuBank tipo=despesa status=confirmado
```

Parâmetros comuns:

```text id="c2v7kp"
conta=NuBank | cartao=NuBank | tipo=despesa | status=previsto | parcelas=10 | recorrente=mensal | ativo=HGLG11
```

Outros:

```text id="m5x9qb"
id=123 | ref=456 | pessoa=João | local=Casa | reembolsavel=true | obs="Compra para viagem"
```

Tags:

```text id="r4k8zn"
#casa | #familia | #trabalho | #viagem
```

Exemplo:

```text id="t7p2yc"
2026-10-05 | -300 | Jantar | Alimentação > Restaurante | conta=NuBank #familia #lazer
```

---

## 17. Estornos e reembolsos

Estorno:

```text id="g6n1vx"
2026-10-10 | 150 | Estorno Mercado | Receitas > Estornos | tipo=estorno ref=123
```

Reembolso:

```text id="p8c4mz"
2026-10-12 | 100 | Reembolso | Receitas > Reembolsos | tipo=receita reembolsavel=true
```

---

## 18. Dashboard

O painel deve mostrar:

```text id="s3w7kp"
saldo atual | receitas | despesas | investimentos | saldo projetado | contas futuras | cartão | patrimônio líquido
```

Exemplo:

```text id="y9m2qc"
Saldo atual: R$ 4.500
Receitas: R$ 8.000
Despesas: R$ 3.200
Investimentos: R$ 2.000
Saldo projetado: R$ 3.100
```

---

## 19. Relatórios

Relatórios:

```text id="v6k1rx"
categorias | subcategorias | receitas | despesas | fluxo de caixa | evolução mensal | investimentos | patrimônio | cartões | parcelas | financiamentos | recorrentes | orçamento
```

Exemplo:

```text id="n3q8yb"
Alimentação: R$ 850
Moradia: R$ 1.500
Transporte: R$ 400
Lazer: R$ 250
```

---

## 20. Orçamento

Pode definir limites por categoria ou subcategoria.

Exemplo:

```text id="f7m2xc"
Alimentação | orçamento=1000
Alimentação > Mercado | orçamento=600
Lazer | orçamento=300
```

Resultado:

```text id="k9v4ps"
Orçamento: R$ 1.000 | Gasto: R$ 850 | Restante: R$ 150
```

---

## 21. Arquivos

Estrutura:

```text id="w2n6qr"
financeiro/
├── dados.md
├── categorias.md
├── contas.md
├── cartoes.md
├── investimentos.md
├── financiamentos.md
└── configuracao.md
```

Exemplo de `dados.md`:

```text id="a5x8km"
2026-10-05 | 8000 | Salário | Receitas > Salário | conta=Itaú tipo=receita
2026-10-05 | -150 | Mercado | Alimentação > Mercado | conta=NuBank tipo=despesa
2026-10-07 | -500 | Transferência | Transferência > Entre contas | tipo=transferencia conta=NuBank destino=Itaú
2026-10-08 | -1000 | Aporte | Investimentos > FIIs | tipo=investimento ativo=HGLG11
2026-10-10 | -1200 | Aluguel | Moradia > Aluguel | recorrente=mensal status=previsto
```

---

## 22. Interface HTML

Funções:

```text id="q8v3mn"
adicionar | editar | excluir | cancelar | duplicar | parcelar | recorrência | transferência | investimento | resgate | cartão | filtros | dashboard | relatórios
```

Exemplo:

Ao escolher `investimento`, o formulário mostra:

```text id="c5k9xr"
Ativo | Quantidade | Preço unitário | Conta | Tipo
```

Ao escolher `despesa`:

```text id="m7p2wb"
Descrição | Valor | Categoria | Subcategoria | Conta | Cartão | Parcelas | Data
```

Ao escolher `transferencia`:

```text id="x4n8qc"
Conta origem | Conta destino | Valor | Data
```

Ao escolher `financiamento`:

```text id="r6v1zk"
Valor | Parcela | Juros | Amortização | Taxas | Saldo devedor
```

### Objetivo

Ter a simplicidade do **MoneyLog**, mas com:

```text id="b3q7mx"
lançamentos | categorias | subcategorias | contas | cartões | parcelas | recorrências | financiamentos | empréstimos | investimentos | patrimônio | orçamento | dashboard | relatórios
```

