# Doctor Schedule

Projeto backend para gerenciamento de clínicas, médicos, pacientes e agendamentos usando **Drizzle ORM** com banco PostgreSQL.

---

## Descrição

Esta aplicação gerencia:

- Usuários e sua relação com clínicas
- Clínicas médicas
- Médicos vinculados a clínicas, com disponibilidade e especialidades
- Pacientes associados às clínicas
- Agendamentos de consultas entre pacientes e médicos

O backend utiliza o Drizzle ORM para definir o schema e relacionamentos, garantindo integridade referencial e controle de dados.

---

## Estrutura do Banco de Dados

### Tabelas principais:

- **users**: Usuários do sistema, identificados por UUID.
- **clinics**: Clínicas médicas, com nome, data de criação/atualização.
- **users_to_clinics**: Relacionamento N:N entre usuários e clínicas.
- **doctors**: Médicos, com dados de disponibilidade, especialidade e preço da consulta.
- **patients**: Pacientes vinculados a clínicas, com nome, email, telefone e sexo (enum: male/female).
- **appointments**: Agendamentos entre pacientes e médicos em clínicas específicas, com data/hora.

---

## Tecnologias usadas

- [Drizzle ORM](https://orm.drizzle.team/) para modelagem e queries no PostgreSQL
- PostgreSQL como banco de dados relacional
- TypeScript para tipagem segura

---

## Como rodar o projeto

1. Configure seu banco PostgreSQL local ou na nuvem.
2. Ajuste as credenciais de conexão no arquivo de configuração (exemplo `.env`).
3. Rode as migrations para criar as tabelas baseadas no schema.
4. Inicie o servidor (ex: `npm run dev`).

---

## Modelagem das entidades (exemplo de campos principais)

| Tabela           | Campos principais                                       | Observações                        |
| ---------------- | ------------------------------------------------------- | ---------------------------------- |
| users            | id (UUID)                                               | Chave primária                     |
| clinics          | id, name, createdAt, updatedAt                          |                                    |
| users_to_clinics | userId (FK), clinicId (FK), timestamps                  | Relacionamento muitos-para-muitos  |
| doctors          | id, clinicId, name, especiality, disponibilidade, preço | Disponibilidade em dias e horários |
| patients         | id, clinicId, name, email, phoneNumber, sex             | sex é enum ['male', 'female']      |
| appointments     | id, date, clinicId, patientId, doctorId                 | Agendamentos vinculados            |

---

## Como contribuir

1. Fork este repositório.
2. Crie uma branch com sua feature: `git checkout -b minha-feature`
3. Faça commit das suas mudanças: `git commit -m 'Minha feature'`
4. Envie para o repositório remoto: `git push origin minha-feature`
5. Abra um Pull Request

---

## Links úteis

- [Documentação Drizzle ORM](https://orm.drizzle.team/)
- [PostgreSQL](https://www.postgresql.org/)
- [Next.js](https://nextjs.org/) (caso seu projeto use Next.js)
- [GitHub Issues](https://github.com/seu-usuario/seu-repo/issues) para reportar bugs e melhorias

---

## Licença

Este projeto está licenciado sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.

---

Feito com ❤️ por você!
