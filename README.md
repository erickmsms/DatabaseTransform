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



## 📇 Dashboard Final

<img width="1264" height="700" alt="DB_AnaliseEmpresarial" src="https://github.com/user-attachments/assets/db4e234e-67a2-44c4-9abc-32711fcee360" />



