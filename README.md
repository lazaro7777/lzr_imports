<!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>LZR_IMPORTS | Camisas de Time</title>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;600&display=swap" rel="stylesheet" />
  <style>
    * {
      box-sizing: border-box;
    }
    body {
      font-family: 'Poppins', sans-serif;
      margin: 0;
      background: #f7f7f7;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
    }
    header,
    footer {
      background: #111;
      color: white;
      text-align: center;
      padding: 20px;
      flex-shrink: 0;
    }
    nav {
      background: #222;
      display: flex;
      justify-content: center;
      gap: 15px;
      padding: 10px;
      flex-shrink: 0;
      flex-wrap: wrap;
    }
    nav a {
      color: white;
      text-decoration: none;
      font-weight: 600;
      cursor: pointer;
      padding: 8px 12px;
      border-radius: 4px;
      transition: background 0.3s;
    }
    nav a:hover {
      background: #25d366;
    }
    .container {
      max-width: 1200px;
      margin: auto;
      padding: 20px;
      flex-grow: 1;
    }
    h2 {
      text-align: center;
      margin-bottom: 20px;
    }
    .camisas {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
      gap: 20px;
    }
    .camisa {
      background: white;
      border-radius: 8px;
      box-shadow: 0 2px 8px rgba(0, 0, 0, 0.12);
      text-align: center;
      padding-bottom: 10px;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
    }
    .camisa img {
      width: 100%;
      border-radius: 8px 8px 0 0;
      object-fit: cover;
      max-height: 260px;
    }
    .camisa h3 {
      margin: 10px 0 5px;
      font-size: 1.1rem;
    }
    .camisa p {
      font-weight: 600;
      color: #25d366;
      margin: 0 0 10px;
      font-size: 1.1rem;
    }
    .add-carrinho {
      background: #25d366;
      color: white;
      padding: 10px 15px;
      border: none;
      border-radius: 5px;
      font-weight: 700;
      cursor: pointer;
      margin: 0 15px 15px 15px;
      transition: background 0.3s;
    }
    .add-carrinho:hover {
      background: #1ebe56;
    }
    .pagamento,
    .contato,
    .avaliacoes,
    .historico {
      background: #eee;
      padding: 20px;
      border-radius: 8px;
      margin-top: 40px;
      max-width: 700px;
      margin-left: auto;
      margin-right: auto;
    }
    .filtros {
      text-align: center;
      margin-bottom: 25px;
    }
    .filtros button {
      margin: 5px;
      padding: 8px 18px;
      border: none;
      border-radius: 5px;
      background: #222;
      color: white;
      cursor: pointer;
      font-weight: 600;
      transition: background 0.3s;
    }
    .filtros button:hover {
      background: #25d366;
    }
    .camisa[data-categoria] {
      display: none;
    }
    .camisa.ativa {
      display: flex;
    }
    #carrinho-modal {
      position: fixed;
      top: 0;
      left: 0;
      width: 100vw;
      height: 100vh;
      background: rgba(0, 0, 0, 0.6);
      display: none;
      justify-content: center;
      align-items: center;
      z-index: 2000;
    }
    #carrinho {
      background: white;
      padding: 20px;
      border-radius: 8px;
      width: 90%;
      max-width: 480px;
      max-height: 80%;
      overflow-y: auto;
      display: flex;
      flex-direction: column;
    }
    #carrinho h2 {
      margin-top: 0;
    }
    #lista-carrinho {
      list-style: none;
      padding-left: 0;
      flex-grow: 1;
      margin-bottom: 15px;
    }
    #lista-carrinho li {
      padding: 8px 10px;
      border-bottom: 1px solid #ddd;
      display: flex;
      justify-content: space-between;
      align-items: center;
      font-weight: 600;
    }
    #lista-carrinho li button {
      background: #ff4d4d;
      border: none;
      color: white;
      padding: 5px 9px;
      border-radius: 4px;
      cursor: pointer;
      font-weight: 700;
      font-size: 0.9rem;
      transition: background 0.3s;
    }
    #lista-carrinho li button:hover {
      background: #cc0000;
    }
    #carrinho button {
      margin-top: 5px;
      padding: 10px;
      border: none;
      border-radius: 5px;
      font-weight: 700;
      cursor: pointer;
      transition: background 0.3s;
    }
    #btn-enviar {
      background: #25d366;
      color: white;
      margin-bottom: 10px;
    }
    #btn-enviar:hover {
      background: #1ebe56;
    }
    #btn-fechar {
      background: #555;
      color: white;
    }
    #btn-fechar:hover {
      background: #333;
    }
    form input,
    form textarea {
      padding: 10px;
      border-radius: 5px;
      border: 1px solid #ccc;
      font-size: 1rem;
      width: 100%;
      margin-bottom: 12px;
      resize: vertical;
    }
    form button {
      background: #111;
      color: white;
      border: none;
      padding: 12px;
      border-radius: 6px;
      font-weight: 700;
      cursor: pointer;
      width: 100%;
      font-size: 1.1rem;
      transition: background 0.3s;
    }
    form button:hover {
      background: #25d366;
    }
    /* Loading */
    .loading {
      position: fixed;
      top: 0;
      left: 0;
      width: 100vw;
      height: 100vh;
      background: white;
      z-index: 3000;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1.5rem;
      font-weight: bold;
    }
    /* Avaliações */
    .avaliacao {
      background: white;
      margin: 10px 0;
      padding: 12px 16px;
      border-radius: 6px;
      box-shadow: 0 1px 4px rgba(0,0,0,0.1);
    }
    .avaliacao strong {
      color: #25d366;
    }
    /* Histórico simples */
    .pedido {
      background: white;
      margin: 10px 0;
      padding: 12px 16px;
      border-radius: 6px;
      box-shadow: 0 1px 4px rgba(0,0,0,0.1);
      font-weight: 600;
    }
    /* WhatsApp fixo */
    #whatsapp-fixo {
      position: fixed;
      bottom: 20px;
      right: 20px;
      background: #25d366;
      border-radius: 50%;
      width: 60px;
      height: 60px;
      display: flex;
      justify-content: center;
      align-items: center;
      z-index: 1000;
      box-shadow: 0 2px 8px rgba(0,0,0,0.2);
      cursor: pointer;
      transition: background 0.3s;
    }
    #whatsapp-fixo:hover {
      background: #1ebe56;
    }
    #whatsapp-fixo img {
      width: 35px;
      height: 35px;
    }

    /* Mobile */
    @media (max-width: 600px) {
      nav {
        gap: 8px;
        padding: 8px;
      }
      nav a {
        font-size: 0.9rem;
        padding: 7px 10px;
      }
      .camisas {
        grid-template-columns: 1fr 1fr;
        gap: 15px;
      }
      .camisa img {
        max-height: 180px;
      }
      #carrinho {
        width: 95%;
      }
      .pagamento,
      .contato,
      .avaliacoes,
      .historico {
        padding: 15px;
        margin-top: 30px;
      }
    }
    @media (max-width: 380px) {
      .camisas {
        grid-template-columns: 1fr;
      }
    }
  </style>
</head>
<body onload="carregarSite()">
  <div class="loading" id="loading">Carregando loja...</div>

  <header>
    <h1>LZR_IMPORTS</h1>
    <p>Camisas de Time Nacionais e Internacionais</p>
  </header>

  <nav>
    <a href="#atuais" onclick="filtrar('todas')">Camisas Atuais</a>
    <a href="#retro" onclick="filtrar('retrô')">Camisas Retrô</a>
    <a href="#pagamento">Pagamento</a>
    <a href="#avaliacoes">Avaliações</a>
    <a href="#historico">Histórico</a>
    <a href="#contato">Contato</a>
    <a href="#" onclick="abrirCarrinho()">🛒 Carrinho (<span id="contador">0</span>)</a>
  </nav>

  <div class="container">
    <div class="filtros">
      <button onclick="filtrar('todas')">Todas</button>
      <button onclick="filtrar('brasil')">Nacionais</button>
      <button onclick="filtrar('internacional')">Internacionais</button>
      <button onclick="filtrar('retrô')">Retrô</button>
      <button onclick="filtrar('atual')">Atuais</button>
    </div>

    <section id="atuais">
      <h2>Camisas Atuais</h2>
      <div class="camisas" id="lista-atuais">
        <!-- Populadas pelo JS -->
      </div>
    </section>

    <section id="retro">
      <h2>Camisas Retrô</h2>
      <div class="camisas" id="lista-retro">
        <!-- Populadas pelo JS -->
      </div>
    </section>

    <section class="pagamento" id="pagamento">
      <h2>Formas de Pagamento</h2>
      <ul style="list-style:none; padding-left: 0;">
        <li>✅ Pix (à vista com confirmação imediata)</li>
        <li>✅ Boleto Bancário</li>
        <li>✅ Cartão (via intermediadores com recebimento integral)</li>
      </ul>
    </section>

    <section class="avaliacoes" id="avaliacoes">
      <h2>Avaliações de Clientes</h2>
      <div id="lista-avaliacoes">
        <!-- Populadas pelo JS -->
      </div>
    </section>

    <section class="historico" id="historico">
      <h2>Histórico de Pedidos</h2>
      <div id="lista-historico">
        <!-- Populadas pelo JS -->
      </div>
    </section>

    <section class="contato" id="contato">
      <h2>Fale Conosco</h2>
      <form id="form-contato">
        <input type="text" name="nome" placeholder="Seu nome" required />
        <input type="email" name="email" placeholder="Seu email" required />
        <textarea name="mensagem" rows="4" placeholder="Sua mensagem" required></textarea>
        <button type="submit">Enviar</button>
      </form>
    </section>
  </div>

  <footer>
    <p>&copy; 2025 LZR_IMPORTS - Todos os direitos reservados.</p>
  </footer>

  <a
    id="whatsapp-fixo"
    href="https://wa.me/17317077457"
    target="_blank"
    title="Fale conosco no WhatsApp"
    ><img
      src="https://cdn-icons-png.flaticon.com/512/733/733585.png"
      alt="WhatsApp"
  /></a>

  <!-- Modal do Carrinho -->
  <div id="carrinho-modal">
    <div id="carrinho">
      <h2>Seu Carrinho</h2>
      <ul id="lista-carrinho
