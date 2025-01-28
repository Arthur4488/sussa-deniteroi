<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Sistema de Gestão de Cargos e Carreira</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <header>
    <h1>Sistema de Gestão de Cargos e Carreira</h1>
    <nav>
      <ul>
        <li><a href="#">Início</a></li>
        <li><a href="#">Profissionais</a></li>
        <li><a href="#">Relatórios</a></li>
      </ul>
    </nav>
  </header>

  <main>
    <section id="filtros">
      <input type="text" placeholder="Nome">
      <select>
        <option value="">Especialidade</option>
        <option value="enfermagem">Enfermagem</option>
        <option value="medicina">Medicina</option>
      </select>
      <button>Filtrar</button>
    </section>

    <section id="tabela-profissionais">
      <table>
        <thead>
          <tr>
            <th>Nome</th>
            <th>Especialidade</th>
            <th>Carga Horária</th>
            <th>Unidade</th>
            <th>Ações</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>João Silva</td>
            <td>Enfermagem</td>
            <td>40h</td>
            <td>UBS Centro</td>
            <td>
              <button>Editar</button>
              <button>Excluir</button>
            </td>
          </tr>
        </tbody>
      </table>
      <button id="adicionar-profissional">Adicionar Profissional</button>
    </section>
  </main>
</body>
</html>
