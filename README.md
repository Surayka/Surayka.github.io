<!DOCTYPE html>
<html lang="sk">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Tréningový a Stravovací Checklist</title>
<style>
  body {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
      Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
    margin: 0;
    padding: 0;
    background: #f9f9f9;
    color: #222;
  }
  header {
    background: #2d89ef;
    color: white;
    padding: 1rem;
    text-align: center;
    font-size: 1.5rem;
    font-weight: 600;
  }
  main {
    max-width: 600px;
    margin: 1rem auto;
    padding: 1rem;
    background: white;
    border-radius: 8px;
    box-shadow: 0 0 10px rgb(0 0 0 / 0.1);
  }
  h2 {
    border-bottom: 2px solid #2d89ef;
    padding-bottom: 0.3rem;
  }
  ul {
    list-style: none;
    padding-left: 0;
  }
  li {
    margin: 0.7rem 0;
    display: flex;
    align-items: center;
  }
  label {
    flex-grow: 1;
    cursor: pointer;
  }
  input[type="checkbox"] {
    margin-right: 1rem;
    width: 1.2rem;
    height: 1.2rem;
    cursor: pointer;
  }
  textarea {
    width: 100%;
    height: 70px;
    margin-top: 0.5rem;
    font-size: 1rem;
    padding: 0.5rem;
    border: 1px solid #ddd;
    border-radius: 6px;
    resize: vertical;
  }
  footer {
    text-align: center;
    margin-top: 2rem;
    font-size: 0.8rem;
    color: #666;
  }
  @media (max-width: 400px) {
    main {
      margin: 0.5rem;
      padding: 0.7rem;
    }
  }
</style>
</head>
<body>
<header>Tréningový a Stravovací Checklist</header>
<main>
  <section id="training">
    <h2>Tréningy - týždeň 1</h2>
    <ul>
      <li><label><input type="checkbox" data-id="pondelok">Pondelok - Spodné telo + core</label></li>
      <li><label><input type="checkbox" data-id="utorok">Utorok - Kardio + mobilita + core</label></li>
      <li><label><input type="checkbox" data-id="streda">Streda - Vrch tela (upravené pre krčnú chrbticu)</label></li>
      <li><label><input type="checkbox" data-id="stvrtok">Štvrtok - Core + mobilita + jemný pohyb</label></li>
      <li><label><input type="checkbox" data-id="piatok">Piatok - Full body</label></li>
      <li><label><input type="checkbox" data-id="sobota">Sobota - Kardio + ľahké posilko</label></li>
      <li><label><input type="checkbox" data-id="nedeľa">Nedeľa - Voľno / joga / strečing</label></li>
    </ul>
  </section>

  <section id="meals">
    <h2>Jedlá - týždeň 1</h2>
    <ul>
      <li><label><input type="checkbox" data-id="ranajky">Raňajky (Herbalife + vločky + orechy + ovocie)</label></li>
      <li><label><input type="checkbox" data-id="desiata">Desiata (Tvaroh, orechy, ovocie)</label></li>
      <li><label><input type="checkbox" data-id="obed">Obed (Tortilla + cottage + zelenina + mäso)</label></li>
      <li><label><input type="checkbox" data-id="olovrant">Olovrant (Proteínový koktejl, orechy)</label></li>
      <li><label><input type="checkbox" data-id="vecera">Večera (Tuniak, cottage, špenát / tortilla s volským okom)</label></li>
    </ul>
  </section>

  <section id="notes">
    <h2>Poznámky na dnes</h2>
    <textarea id="noteText" placeholder="Napíš si sem poznámky..."></textarea>
  </section>
</main>

<footer>
  &copy; 2025 Tvoj Tréningový Asistent
</footer>

<script>
  // Load saved checklist and note from localStorage
  window.addEventListener('DOMContentLoaded', () => {
    document.querySelectorAll('input[type=checkbox]').forEach(chk => {
      const id = chk.dataset.id;
      const saved = localStorage.getItem('check_' + id);
      if (saved === 'true') {
        chk.checked = true;
      }
      chk.addEventListener('change', () => {
        localStorage.setItem('check_' + id, chk.checked);
      });
    });

    const noteArea = document.getElementById('noteText');
    const savedNote = localStorage.getItem('noteText');
    if (savedNote) noteArea.value = savedNote;

    noteArea.addEventListener('input', () => {
      localStorage.setItem('noteText', noteArea.value);
    });
  });
</script>
</body>
</html>
