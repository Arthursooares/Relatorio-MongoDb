#  Desafio Banco de Dados – Empresa Momento

##  Nível 1 – Conhecendo a Empresa

### 1.1 Inserir suas informações
```js
db.funcionarios.insertOne({
  nome: "Arthur",
  sobrenome: "Soares",
  data_nascimento: "2003-10-28",
  data_contratacao: "2020-01-01",
  salario: 5000,
  departamento: "Tecnologia",
  cargo: "Desenvolvedor",
  escritorio: "São Paulo"
})
1.2 Total de funcionários
24 funcionários

1.3 Funcionários em Tecnologia
5 funcionários
(Alexander Hunold, Bruce Ernst, David Austin, Valli Stark, Diana Lorentz)

1.4 Departamentos existentes
Executivo, Vendas, Marketing, Financeiro, Tecnologia, Recursos Humanos, Dados
→ Total: 7 departamentos

1.5 Escritórios e países
Escritório	País
Wayne Offices	USA
Winterfell Offices	IRE
Stark Industries	ENG
Umbrella Corp	EQU

💰 Nível 2 – Análise Financeira
2.1 Funcionários em Vendas
10 funcionários

2.2 Custo total com salários – Vendas
R$ 90.100

2.3 Média salarial da empresa (sem CEO, CMO, CFO)
R$ 11.404

2.4 Média salarial de Tecnologia
R$ 4.960

2.5 Departamento com maior média salarial
Executivo (R$ 71.000)

2.6 Departamento com menor número de funcionários
Dados

👥 Nível 3 – Recursos Humanos
3.1 Funcionários com cônjuge
7 funcionários

3.2 Funcionários com filhos
7 funcionários

3.3 Funcionário com mais tempo de casa
Irene Adler (1980-09-28)

3.4 Funcionário mais recente
Valli Stark (2009-02-05)

3.5 Top 5 com mais tempo de casa
Irene Adler (1980)

Jennifer Whalen (1987)

Den Raphaely (1994)

Normam Osborn (1995)

Matthew Weiss (1996)

3.6 Contratados na década de 1990
9 funcionários

3.7 Evolução da média salarial
Ano	Média Salarial
1980	9700
1987	23000
1994	12500
1995	18080
1996	37233
1997	10266
1999	8900
2000	4100
2005	3400
2008	3500
2009	2900

🏢 Nível 4 – Operações e Escritórios
4.1 Escritórios e países
Escritório	País
Wayne Offices	USA
Winterfell Offices	IRE
Stark Industries	ENG
Umbrella Corp	EQU

4.2 Custo total de suprimentos
Escritório	Total ($)
Umbrella Corp	376.425.000
Stark Industries	105.392,5
Wayne Offices	65.805
Winterfell Offices	65.305

4.3 Escritório com mais tipos de suprimentos
Empate entre Wayne, Winterfell e Stark (5 tipos cada)

4.4 Suprimento mais caro (unitário)
Computadores – $5.000

4.5 Valor total do inventário
$376.661.202,50

🛒 Nível 5 – Produtos e Vendas
5.1 Produtos vendidos
Uniforme do Superman

Fake Batarang

Lança-Teias

Capacete do Homem-Formiga

Nulificador Total

Laço da Verdade

Sabre de Luz (Mace Windu)

Sentinelas do Bolivar Trask

Uniforme de Moléculas Instáveis

→ 9 produtos únicos

5.2 Produto mais vendido
Sentinelas do Bolivar Trask (9 unidades)

5.3 Produto menos vendido
Uniforme do Superman (2 unidades)

5.4 Produto com maior receita
Sabre de Luz (8 × 990.29 = $7.922,32)

5.5 Produto mais caro (unitário)
Sabre de Luz (Mace Windu) – $990,29

5.6 Faturamento total
$28.392,45

5.7 Vendas em junho de 2023
5 vendas

5.8 Vendedor com mais vendas
Jon Deegan (2 vendas)

5.9 Vendedor com maior receita
Michael Hartstein – $7.922,32

⚙️ Nível 6 – Atualizações
6.1 Criar o departamento “Inovações”
js
Copiar código
db.departamentos.insertOne({
  nome: "Inovações",
  escritorio: ObjectId("5f8b3f3f9b3e0b3b3c1e3e3e")
})
6.2 Transferir 2 funcionários para Inovações
js
Copiar código
db.funcionarios.updateMany(
  { nome: { $in: ["Alexander Hunold", "Bruce Ernst"] } },
  { $set: { departamento: "Inovações" } }
)
6.3 Aumento de 10% para Tecnologia
js
Copiar código
db.funcionarios.updateMany(
  { departamento: "Tecnologia" },
  { $mul: { salario: 1.1 } }
)
6.4 Promover Bruce Ernst
js
Copiar código
db.funcionarios.updateOne(
  { nome: "Bruce Ernst" },
  { $set: { cargo: "Senior Web Developer", salario: 5000 } }
)
6.5 Adicionar suprimentos (Headsets) ao Wayne Offices
js
Copiar código
db.escritorios.updateOne(
  { nome: "Wayne Offices" },
  { $push: { suprimentos: { produto: "Headsets", quantidade: 15, precoUnitario: 150 } } }
)
6.6 Remover funcionários contratados antes de 1990
js
Copiar código
db.funcionarios.deleteMany({ dataAdmissao: { $lt: "1990-01-01" } })
→ Afetados: Irene Adler (1980) e Jennifer Whalen (1987)

🧾 Conclusão
Total de funcionários: 21

Total de departamentos: 7

Total de escritórios: 4

Faturamento total: $28.392,45

Inventário total: $376.661.202,50

Departamento com melhor média: Executivo

Funcionário mais antigo: Irene Adler

Produto mais lucrativo: Sabre de Luz (Mace Windu)

Escritório mais caro: Umbrella Corp

yaml
Copiar código

