# Hotel-Nebula

Projeto de estruturação e análise de dados para a rede **Hotel Nebula** utilizando **MongoDB**. O objetivo é organizar as operações do hotel (reservas, hospedagens, pagamentos e avaliações) em um banco não relacional para suportar uma futura API de gestão.

---

## Estrutura do Projeto

* **`parte-1-modelagem/`**: Documentação das 8 coleções, justificativas de modelagem (uso de referências vs. documentos embutidos) e exemplos em JSON.
* **`parte-2-implementacao/seed.js`**: Script em JavaScript para criar o banco `hotel_nebula` e inserir os dados iniciais nas coleções.
* **`parte-3-consultas/consultas.js`**: Consultas e agregações para relatórios gerenciais (busca de quartos, clientes recorrentes, faturamento e ocupação).

---

## Resumo da Arquitetura

O banco `hotel_nebula` possui **8 coleções** principais, combinando **referências (`ObjectId`)** e **dados embutidos**:

1. **`hospedes`**: Cadastro de clientes (com `endereco` e `preferencias` embutidos).
2. **`quartos`**: Dados dos quartos, `comodidades` (array) e `caracteristicas`.
3. **`funcionarios`**: Equipe do hotel, `turno` e `permissoes`.
4. **`servicos`**: Catálogo de serviços extras (café da manhã, lavanderia, minibar).
5. **`reservas`**: Referencia hóspede e quarto, mas guarda um `snapshot` (cópia) dos dados da época da reserva para manter o histórico.
6. **`hospedagens`**: Check-in/check-out reais e array de `servicos_consumidos` durante a estadia.
7. **`pagamentos`**: Valores pagos, nota fiscal e array de `parcelas`/métodos de pagamento.
8. **`feedbacks`**: Avaliações em coleção própria (para não sobrecarregar o documento do quarto) e respostas do hotel.

---

## Como Executar

1. Abra o **MongoDB Compass** (ou terminal com `mongosh`) e conecte-se ao seu banco.
2. Execute o script `parte-2-implementacao/seed.js` para criar as coleções e popular os dados.
3. Rode os comandos de `parte-3-consultas/consultas.js` para visualizar os relatórios de gestão.
