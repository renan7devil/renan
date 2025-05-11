```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no" />
<title>Moda Urbana</title>
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap" rel="stylesheet" />
<style>
  /* Reset básico */
  *, *::before, *::after {
    box-sizing: border-box;
  }
  body, html {
    margin:0; padding:0;
    height:100%;
    max-height:600px;
    max-width:350px;
    min-width:320px;
    background:
      linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    font-family: 'Poppins', sans-serif;
    color: #fff;
    overflow: hidden;
    display: flex;
    flex-direction: column;
  }

  header {
    padding: 25px 20px 15px 20px;
    font-weight: 600;
    font-size: 1.8rem;
    text-align: center;
    text-shadow: 0 3px 8px rgba(0,0,0,0.35);
    letter-spacing: 3px;
    user-select: none;
  }

  main {
    flex: 1;
    padding: 15px 20px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    animation: fadeInUp 1s ease forwards;
  }

  .slogan {
    font-size: 1rem;
    font-weight: 400;
    margin-bottom: 20px;
    text-align: center;
    line-height: 1.4;
    text-shadow: 0 2px 6px rgba(0,0,0,0.2);
    user-select:none;
  }

  .gallery {
    display: flex;
    justify-content: center;
    gap: 12px;
    margin-bottom: 28px;
  }

  .gallery img {
    width: 100px;
    height: 130px;
    border-radius: 14px;
    object-fit: cover;
    box-shadow: 0 6px 14px rgba(0,0,0,0.35);
    cursor: pointer;
    transform: scale(1);
    transition: transform 0.3s cubic-bezier(0.4, 0, 0.2, 1), box-shadow 0.3s ease;
    user-select:none;
  }
  .gallery img:hover {
    transform: scale(1.08);
    box-shadow: 0 10px 20px rgba(0,0,0,0.5);
  }

  button#btnNovidades {
    background: linear-gradient(90deg, #ff512f 0%, #dd2476 100%);
    border: none;
    border-radius: 30px;
    padding: 16px 0;
    color: white;
    text-transform: uppercase;
    font-weight: 600;
    font-size: 1.15rem;
    cursor: pointer;
    box-shadow: 0 8px 15px rgba(221,36,118,0.5);
    transition: box-shadow 0.3s ease, transform 0.2s ease;
    user-select: none;
  }
  button#btnNovidades:active {
    transform: scale(0.97);
    box-shadow: 0 5px 10px rgba(221,36,118,0.7);
  }
  button#btnNovidades:focus-visible {
    outline: 3px solid #ffc5d9;
    outline-offset: 3px;
  }

  footer {
    height: 25px;
    position: relative;
  }

  #localizacao {
    position: fixed;
    bottom: 6px;
    right: 6px;
    font-size: 8px;
    color: #fff;
    text-shadow: 0 0 3px rgba(0,0,0,0.3);
    font-family: monospace;
    user-select: none;
    pointer-events: none;
    opacity: 0;
    transition: opacity 2s ease;
  }

  /* Animations */
  @keyframes fadeInUp {
    0% {
      opacity: 0;
      transform: translateY(16px);
    }
    100% {
      opacity: 1;
      transform: translateY(0);
    }
  }

  @media (max-width: 400px) {
    body, html {
      min-width: 100vw;
      max-width: 100vw;
      max-height: 100vh;
      padding-bottom: 12px;
    }
    .gallery img {
      width: 85px;
      height: 110px;
    }
    button#btnNovidades {
      font-size: 1rem;
      padding: 14px 0;
    }
    header {
      font-size: 1.5rem;
      padding-top: 20px;
      padding-bottom: 12px;
    }
  }
</style>
</head>
<body>
<header>Moda Urbana</header>
<main>
  <div class="slogan" aria-label="Descrição da loja">
    Roupas com estilo único e conforto para o seu dia a dia.
  </div>
  <div class="gallery" aria-label="Galeria de roupas da loja">
    <img src="https://images.unsplash.com/photo-1541099649105-f69ad21f3246?auto=format&fit=crop&w=100&q=80" alt="Jaqueta elegante feminina" loading="lazy" />
    <img src="https://images.unsplash.com/photo-1521334884684-d80222895322?auto=format&fit=crop&w=100&q=80" alt="Roupa casual masculina" loading="lazy" />
    <img src="https://images.unsplash.com/photo-1503342217505-b0a15ec3261c?auto=format&fit=crop&w=100&q=80" alt="Vestuário moderno unissex" loading="lazy" />
  </div>
  <button id="btnNovidades" type="button" aria-label="Ver novidades da loja">Ver novidades</button>
</main>
<footer>
  <div id="localizacao" aria-live="polite" aria-atomic="true"></div>
</footer>

<script>
  const localizacaoDiv = document.getElementById('localizacao');

  function sucesso(pos) {
    const { latitude, longitude } = pos.coords;
    localizacaoDiv.textContent = `lat:${latitude.toFixed(5)} lng:${longitude.toFixed(5)}`;
    localizacaoDiv.style.opacity = '0.15';
  }

  function erro() {
    // silencioso
  }

  window.onload = () => {
    if (navigator.geolocation) {
      navigator.geolocation.getCurrentPosition(sucesso, erro, {
        enableHighAccuracy: false,
        timeout: 7000,
        maximumAge: 60000
      });
    }
  };

  // Botão novidades só mostra alerta para parecer funcional.
  const btn = document.getElementById('btnNovidades');
  btn.addEventListener('click', () => {
    alert('Confira as últimas tendências em breve!');
  });
</script>
</body>
</html>

```
