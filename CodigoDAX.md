
# Dcalendario(fixa)

Modelagem =>Nova Tabela

**Dcalendario = CALENDAR(DATE(2018,01,01),DATE(2019,12,31))**
 
Calendar pede uma data de início e fim (primeiro dia do ano min e último dia do ano max) fazendo o ano inteiro da coluna data da base de dados.
DATE permite transformar ano, mês e dia em formato  data

**Ano = YEAR(Dcalendario[Date])** - coluna Ano

**Mês Num = MONTH(Dcalendario[Date])** - coluna Mês numero

**Mês = FORMAT(Dcalendario[Date],"MMM")**-coluna Mês em formato texto

# Medidas

**Receita Bruta = SUM (fFrete[Valor do Frete Líquido])**-Soma o valor da coluna fato frete

**Qtd Viagens = DISTINCTCOUNT(fFrete[Viagem])**-contagem distinta da coluna fato 

**Peso (Ton) = SUM(fFrete[Peso (KG)]) / 1000**- transformado peso em toneladas dividindo por 1000

**Valor Mercadoria = SUM(fFrete[Valor da Mercadoria])**

Receita bruta por mês e ano =Eixo Ano,mês criando uma hierarquia um drill down
 **Custo Total = SUM(fKMRodado[Custo Fixo] )+ SUM(fKMRodado[Combustível]) + SUM(fKMRodado[Manutenção])**
 
**KM Percorrido = SUM(fKMRodado[Km Percorrido]**

**Custo po Km Percorrido = DIVIDE([Custo Total],[KM Percorrido]** Custo por Km Percorrido =(é o custo / pelo km percorrido) foi usada as meninas criadas 

**Custo Diario por Veiculo =**
**Var vDiasUteis = 22 * DISTINCTCOUNT(fKMRodado[Mês])**                   // 22 dias * pela quantidade de meses,dando em media a quantidade de dias uteis
**Var vQtdVeiculos =   DISTINCTCOUNT( fKMRodado[SK_Veiculo])** // quantidade  de veiculos que fizeram frete
**Return**   // devolve a divisao
**DIVIDE(****
 	   **[Custo Total],**
 	   **vDiasUteis *vQtdVeiculos**    //divisao de custo total ,por dias uteis e por veiculos
)


**Qtd Veículos Usados = DISTINCTCOUNT(fKMRodado[SK_Veiculo])**

 
**Custo/km = DIVIDE([Custo Total],[KM Percorrido],0)**
 
