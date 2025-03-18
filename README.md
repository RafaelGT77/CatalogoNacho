<!DOCTYPE html>
<html lang="es">
    <link rel="stylesheet" href="styles.css">

<head>
  <meta charset="UTF-8">
  <title>Catálogo de Productos</title>
</head>
<body>
  <h1>Catálogo de Productos - Nacho Haro</h1>

  <!-- Área de catálogo -->
  <section id="catalog-area">
    <!-- Campo de venta: Electrónicos -->
    <article id="catalog-electronics">
      <h2>Electrónicos</h2>
      <p>Celulares: <span id="cellphone-count">Sin stock</span></p>
      <p>Computadoras: <span id="computer-count">Sin stock</span></p>
      <p>Tablets: <span id="tablet-count">Sin stock</span></p>
    </article>

    <!-- Campo de venta: Ropa -->
    <article id="catalog-clothing">
      <h2>Ropa</h2>
      <p>Camisas: <span id="shirt-count">Sin stock</span></p>
      <p>Pantalones: <span id="pants-count">Sin stock</span></p>
      <p>Zapatos: <span id="shoes-count">Sin stock</span></p>
    </article>

    <!-- Campo de venta: Hogar -->
    <article id="catalog-home">
      <h2>Hogar</h2>
      <p>Sillas: <span id="chair-count">Sin stock</span></p>
      <p>Mesas: <span id="table-count">Sin stock</span></p>
      <p>Lámparas: <span id="lamp-count">Sin stock</span></p>
    </article>
  </section>

  <!-- Botón para acceder al panel de administración -->
  <button id="open-admin-btn">Abrir Panel de Administración</button>

  <!-- Panel de Administración -->
  <section id="admin-panel" style="display: none; margin-top:20px;">
    <!-- Sección de login -->
    <div id="login">
      <h2>Acceso Administrativo</h2>
      <label for="admin-password">Ingrese la contraseña:</label>
      <input type="password" id="admin-password">
      <button id="login-btn">Entrar</button>
    </div>

    <!-- Contenido del panel (oculto hasta validar contraseña) -->
    <div id="admin-content" style="display: none;">
      <h2>Actualizar Inventario</h2>
      <form id="inventory-form">
        <!-- Electrónicos -->
        <h3>Electrónicos</h3>
        <label for="admin-cellphone">Celulares:</label>
        <input type="number" id="admin-cellphone" min="0" value="0"><br>
        <label for="admin-computer">Computadoras:</label>
        <input type="number" id="admin-computer" min="0" value="0"><br>
        <label for="admin-tablet">Tablets:</label>
        <input type="number" id="admin-tablet" min="0" value="0"><br>
        <!-- Ropa -->
        <h3>Ropa</h3>
        <label for="admin-shirt">Camisas:</label>
        <input type="number" id="admin-shirt" min="0" value="0"><br>
        <label for="admin-pants">Pantalones:</label>
        <input type="number" id="admin-pants" min="0" value="0"><br>
        <label for="admin-shoes">Zapatos:</label>
        <input type="number" id="admin-shoes" min="0" value="0"><br>
        <!-- Hogar -->
        <h3>Hogar</h3>
        <label for="admin-chair">Sillas:</label>
        <input type="number" id="admin-chair" min="0" value="0"><br>
        <label for="admin-table">Mesas:</label>
        <input type="number" id="admin-table" min="0" value="0"><br>
        <label for="admin-lamp">Lámparas:</label>
        <input type="number" id="admin-lamp" min="0" value="0"><br><br>
        <button type="button" id="update-inventory">Actualizar Inventario</button>
      </form>
    </div>
  </section>

  <script>
    // Objeto que contiene el inventario de cada producto
    let inventory = {
      cellphone: 0,
      computer: 0,
      tablet: 0,
      shirt: 0,
      pants: 0,
      shoes: 0,
      chair: 0,
      table: 0,
      lamp: 0
    };

    // Función para actualizar la visualización del catálogo
    function updateCatalogDisplay() {
      document.getElementById("cellphone-count").textContent = inventory.cellphone > 0 ? inventory.cellphone : "Sin stock";
      document.getElementById("computer-count").textContent = inventory.computer > 0 ? inventory.computer : "Sin stock";
      document.getElementById("tablet-count").textContent = inventory.tablet > 0 ? inventory.tablet : "Sin stock";
      document.getElementById("shirt-count").textContent = inventory.shirt > 0 ? inventory.shirt : "Sin stock";
      document.getElementById("pants-count").textContent = inventory.pants > 0 ? inventory.pants : "Sin stock";
      document.getElementById("shoes-count").textContent = inventory.shoes > 0 ? inventory.shoes : "Sin stock";
      document.getElementById("chair-count").textContent = inventory.chair > 0 ? inventory.chair : "Sin stock";
      document.getElementById("table-count").textContent = inventory.table > 0 ? inventory.table : "Sin stock";
      document.getElementById("lamp-count").textContent = inventory.lamp > 0 ? inventory.lamp : "Sin stock";
    }

    // Inicializa la visualización del catálogo
    updateCatalogDisplay();

    // Panel de administración
    const adminPassword = "1234"; // Contraseña predefinida
    document.getElementById("open-admin-btn").addEventListener("click", function() {
      document.getElementById("admin-panel").style.display = "block";
    });

    document.getElementById("login-btn").addEventListener("click", function() {
      const passwordInput = document.getElementById("admin-password").value;
      if (passwordInput === adminPassword) {
        alert("Acceso concedido");
        document.getElementById("login").style.display = "none";
        document.getElementById("admin-content").style.display = "block";
      } else {
        alert("Contraseña incorrecta");
      }
    });

    // Función para actualizar el inventario
    document.getElementById("update-inventory").addEventListener("click", function() {
      inventory.cellphone = parseInt(document.getElementById("admin-cellphone").value);
      inventory.computer = parseInt(document.getElementById("admin-computer").value);
      inventory.tablet = parseInt(document.getElementById("admin-tablet").value);
      inventory.shirt = parseInt(document.getElementById("admin-shirt").value);
      inventory.pants = parseInt(document.getElementById("admin-pants").value);
      inventory.shoes = parseInt(document.getElementById("admin-shoes").value);
      inventory.chair = parseInt(document.getElementById("admin-chair").value);
      inventory.table = parseInt(document.getElementById("admin-table").value);
      inventory.lamp = parseInt(document.getElementById("admin-lamp").value);
      updateCatalogDisplay();
      alert("Inventario actualizado");
    });
  </script>
</body>
</html>
 
