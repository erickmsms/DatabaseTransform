# 🧠 Company Data Transformation Project

Este projeto demonstra o processo completo de **modelagem e transformação de dados relacionais** para integração em um ambiente de **Business Intelligence (Power BI)**.  
A base é composta por dados de uma empresa fictícia com colaboradores, departamentos, dependentes e projetos.

## 🎯 Objetivos

- Validar e padronizar os tipos de dados nas tabelas.
- Tratar valores nulos e definir regras de substituição.
- Modelar relações entre entidades (departamentos, funcionários, projetos, etc).
- Criar consultas SQL para preparar os dados para importação no Power BI.
- Produzir um modelo relacional limpo e pronto para análise.


## 🗃️ Estrutura do Banco de Dados Original

As tabelas originais incluem:

- **employee**
- **department**
- **dependent**
- **dept_locations**
- **project**
- **works_on**

Cada tabela foi inspecionada e validada conforme as diretrizes de transformação.

## 🛠️ O que foi feito?

1. **Extração inicial — juntei Department e Dept_Locations**
   - Para começar puxei os departamentos já combinados com suas localizações diretamente do banco de dados. Usei a query abaixo (executada no banco `azure_company`):
  
   ```sql
   SELECT CONCAT(d.Dname, ' - ', dl.Dlocation) AS Dname,
          d.Dnumber,
          d.Mgr_ssn,
          d.Mgr_start_date,
          d.Dept_create_date
   FROM azure_company.departament d
   INNER JOIN azure_company.dept_locations dl
     ON d.Dnumber = dl.Dnumber;
   ```
2. **Inspeção de cabeçalhos e tipos**
   - Verifiquei cada tabela (employees, dependents, projects, department, dept_locations) para garantir nomes consistentes e tipos corretos (int, varchar, date, double).

3. **Normalização e separação de colunas complexas**
   - Separei colunas como Address em partes (Rua, Cidade, Estado) para facilitar filtros no PowerBI.
  
4. **Mescla de Consultas: Employee ↔ Department**
   - Usei LEFT JOIN (pelo próprio PowerBI) para garantir que todos os empregados aparecessem, mesmo que algum departamento estivesse com inconsistência.

5. **Mescla de Consultas: Employee ↔ Manager**
   - Criei a relação entre funcionário e seu gerente, através de uma autojunção.

6. **Mescla de Colunas: Criação da coluna FullName**
   - Mesclei Fname e Lname em uma única coluna, pela própria função dentro do PowerBI.

7. **Agrupamento**
   - Agrupei os funcionários por gerente para identificar o número de subordinados.

8. **Eliminação de colunas desnecessárias**
   - Removi colunas auxiliares (como Minit, IDs intermediários, etc.), mantendo apenas as informações relevantes para análise.

9. **Criação dos Dashboards**
   - Carreguei os dados limpos, e iniciei as análises.
     

## 📇 Dashboard Final

<img width="1264" height="700" alt="DB_AnaliseEmpresarial" src="https://github.com/user-attachments/assets/db4e234e-67a2-44c4-9abc-32711fcee360" />



