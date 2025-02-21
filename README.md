# API de Gestão de Médicos - Spring Boot

Esta API permite gerenciar médicos em um sistema, fornecendo endpoints para cadastro, listagem, atualização e exclusão de médicos.

## Requisitos

- Java 17 ou superior
- Spring Boot 2.x
- Banco de Dados (configuração com JPA)

## Como rodar o projeto

1. Clone o repositório:

   ```bash
   git clone https://seurepositorio.git
   cd seu-diretorio
   
2. Configure o banco de dados no application.properties:
   spring.datasource.url=jdbc:mysql://localhost:3306/seubanco
   spring.datasource.username=usuario
   spring.datasource.password=senha
   
3. Execute o projeto:
   ./mvnw spring-boot:run

## Endpoints

### 1. Cadastrar Médico

- **URL**: `/medicos`
- **Método**: `POST`
- **Descrição**: Cadastra um novo médico no sistema.
- **Corpo da Requisição**:
  - Exemplo de Dados:
    ```json
    {
      "nome": "Dr. João",
      "crm": "12345",
      "especialidade": "Cardiologia",
      "email": "joao@medicos.com",
      "telefone": "(11) 99999-9999"
    }
    ```

### 2. Listar Médicos

- **URL**: `/medicos`
- **Método**: `GET`
- **Descrição**: Lista médicos ativos com paginação.
- **Parâmetros**:
  - `page`: Página atual (opcional)
  - `size`: Tamanho da página (opcional)
  - `sort`: Ordenação por nome (opcional)

  **Exemplo de Requisição**:
  http
  GET /medicos?page=0&size=10&sort=nome
  
  ### 3. Atualizar Médico

    - ** URL: /medicos **
    - ** Método:** PUT 
    - ** Descrição:** Atualiza as informações de um médico existente.
    - ** Corpo da Requisição: **
        Exemplo de Dados:

        {
          "id": 1,
          "nome": "Dr. João Silva",
          "crm": "12345",
          "especialidade": "Cardiologia",
          "email": "joao.silva@medicos.com",
          "telefone": "(11) 88888-8888"
        }
      
### 4. Excluir Médico

    - ** URL: /medicos/{id} **
    - ** Método: ** DELETE
    - ** Descrição: ** Exclui um médico com o ID fornecido.
    - ** Exemplo de Requisição: **
	http
		DELETE /medicos/1


	
		
### 5. Exemplo de Uso do Map

O código da classe MedicoController utiliza objetos Map em algumas das transformações de dados, por exemplo, ao converter os dados de uma entidade para um DTO. Esses objetos de mapeamento (como ** DadosListagemMedico::new **) são usados para retornar uma representação específica de um médico sem expor diretamente a entidade.

Dados de Cadastro de Médico

A classe DadosCadastroMedico é responsável por armazenar as informações de entrada do novo médico e será utilizada no método cadastrar.
Dados de Listagem de Médico

A classe DadosListagemMedico define como um médico será apresentado na resposta de listagem, podendo incluir apenas informações relevantes como nome, especialidade, e outros campos.
Dependências

    ** Spring Web **
    ** Spring Data JPA **
    ** Jakarta Validation **
