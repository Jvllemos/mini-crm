# Mini-CRM de Leads

Sistema simples de gestão de leads desenvolvido em Lovable com persistência de dados no Supabase.

## Links de Entrega
- **Link do Sistema (Deploy):** [https://lead-trail-keeper.lovable.app]


---

## Diário de Bordo
1. Configurei o banco no Supabase criando a tabela `leads` com restrições para as etapas do funil ('Novo', 'Em contato', 'Fechado') e ativei o acesso via RLS.
2. Integrei o Supabase ao Lovable para construir a interface de cadastro de leads com atualização dinâmica de etapas em tempo real.
3. Testei a persistência dos dados, publiquei a aplicação no Lovable e criei esta branch no GitHub para submeter o Pull Request final.

---

## Perguntas Teóricas

### 1. Onde o dado fica guardado?
O dado fica guardado em um banco de dados relacional **PostgreSQL**, hospedado em nuvem e gerido pela infraestrutura do **Supabase**. O Lovable atua apenas como a camada de interface (Front-end), comunicando-se com a API do Supabase via chamadas HTTP/REST.

### 2. O que acontece se a linha for apagada no Supabase?
Se a linha for excluída diretamente na tabela do Supabase:
- O registro é removido permanentemente do banco de dados PostgreSQL.
- Como a aplicação consulta o Supabase para exibir os dados, o lead desaparecerá da interface assim que a lista for recarregada ou atualizada.
- Qualquer tentativa da aplicação de alterar ou buscar esse lead pelo ID resultará em um erro de registro não encontrado (`404` / `null`).
