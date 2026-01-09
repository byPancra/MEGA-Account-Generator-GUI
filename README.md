<div align="center">

[English](README.md) | [Português (Brasil)](README_pt-BR.md) | **Español** | [日本語](README_ja.md)

</div>
<br>

<div align="center">

  ![Mega Account Generator GUI](./img/readme-icon.png)

  <h1 align="center">Mega Account Generator GUI</h1>
  
  **La herramienta definitiva para la automatización de la creación y gestión de cuentas de MEGA.nz.**
  
  *Genere, Gestione, Etiquete y Exporte sus cuentas con una interfaz de nivel profesional.*

  [![Python Version](https://img.shields.io/badge/python-3.8%2B-blue?style=for-the-badge&logo=python)](https://www.python.org/)
  [![License](https://img.shields.io/badge/license-MIT-green?style=for-the-badge)](./LICENSE)
  [![Status](https://img.shields.io/badge/status-active-success?style=for-the-badge)]()
  [![Releases](https://img.shields.io/github/downloads/byPancra/Mega-Account-Generator-GUI/total?style=for-the-badge&color=orange)](https://github.com/byPancra/Mega-Account-Generator-GUI/releases)

  [Características](#-características) • [Instalación](#-instalación) • [Uso](#-uso) • [Gestión Avanzada](#-gestión-avanzada) • [FAQ](#-faq)

</div>

---

## 📋 Descripción General

**Mega Account Generator GUI** es una aplicación robusta de escritorio diseñada para usuarios avanzados que necesitan generar y gestionar cuentas de [MEGA.nz](https://mega.nz) en masa. A diferencia de scripts simples, esta herramienta proporciona un ecosistema completo para la gestión del ciclo de vida de la cuenta, incluyendo etiquetado, filtrado, seguimiento de estado y exportación de datos.

Construido con **Python Moderno** (CustomTkinter) y **Arquitectura Thread-Safe**, garantiza confiabilidad incluso al procesar cientos de cuentas.

![Demo](./img/intro2.gif)

---

## :zap: Características

### 🚀 Generación Principal
*   **Multi-Threading de Alta Velocidad**: Genere hasta 8 cuentas simultáneamente.
*   **Limitación de Tasa Inteligente**: Retrasos inteligentes y lógica de reintento (hasta 12 intentos) para evitar las restricciones de Mail.tm.
*   **Dependencias Integradas**: La versión ejecutable viene con `megatools` pre-empaquetado—no se requiere configuración externa.

### 🛠️ Gestión Avanzada
*   **Sistema de Etiquetas**: Organice cuentas con etiquetas personalizadas (ej: `Personal`, `Backup`, `Cliente-A`) para facilitar su recuperación.
*   **Búsqueda y Filtro**: Encuentre cuentas instantáneamente por Correo, Estado (`Active`, `Disabled`, `Failed`) o Etiquetas.
*   **Operaciones Masivas**:
    *   **Keep-Alive**: Inicio de sesión automatizado para evitar la eliminación de cuentas por inactividad.
    *   **Verificación de Almacenamiento**: Actualiza automáticamente las cuotas de almacenamiento usado/libre para todas las cuentas.
    *   **Control de Cuentas**: Deshabilite cuentas específicas para excluirlas de operaciones masivas (ej: verificaciones Keep-Alive) sin eliminarlas.

### 💾 Libertad de Datos
*   **Exportación Profesional**: Exporte su base de datos a **Excel (.xlsx)** con estilo formateado o **JSON** para uso programático.
*   **Importación Perfecta**: Migre datos de otras herramientas o copias de seguridad mediante importación JSON/Excel.
*   **Integración con Portapapeles**: Copia con un clic para correos y contraseñas.

### 🔒 Seguridad y Confiabilidad
*   **CSV Thread-Safe**: Previene la corrupción de datos durante escrituras simultáneas.
*   **Recuperación de Fallos**: El botón "Stop" detiene las operaciones con gracia, preservando la integridad de los datos.

---

## :rocket: Instalación

### Opción A: Ejecutable Independiente (Recomendado)
Descargue la última versión. No se necesita Python ni herramientas externas.
1.  Descargue `MegaGenerator.exe` desde [Releases](https://github.com/byPancra/Mega-Account-Generator-GUI/releases).
2.  Ejecute el archivo.

### Opción B: Ejecutando desde el Código Fuente

**Requisitos previos:**
*   Python 3.8+
*   [Megatools](https://megatools.megous.com/) (Agregado al PATH)

**Pasos:**
1.  **Clonar el repositorio:**
    ```bash
    git clone https://github.com/byPancra/Mega-Account-Generator-GUI.git
    cd Mega-Account-Generator-GUI
    ```

2.  **Instalar dependencias:**
    ```bash
    pip install -r requirements.txt
    ```

3.  **Ejecutar la aplicación:**
    ```bash
    python gui.py
    ```

---

## :computer: Uso

### Generando Cuentas
1.  Navegue a la pestaña **Generator**.
2.  Establezca el número de **Threads** (Hilos) y **Accounts** (Cuentas) a generar.
3.  Haga clic en **"Generate Accounts"**.
4.  Las credenciales se guardarán en `accounts.csv` y serán visibles en la pestaña **Stored Accounts**.

### Gestionando Cuentas
Navegue a la pestaña **Stored Accounts**:
*   **Búsqueda**: Escriba un correo para filtrar instantáneamente.
*   **Filtro**: Use el menú desplegable para ver solo cuentas `Active`, `Disabled`, o `Failed`.
*   **Editar**: Haga clic en el botón "Edit" para cambiar una contraseña guardada o gestionar Etiquetas.
*   **Copiar**: Botones rápidos para copiar credenciales al portapapeles.

### 💻 Uso vía CLI (Línea de Comandos)
Para usuarios avanzados que prefieren la terminal o quieren integrar esto en scripts.

```bash
# Uso básico (Gera 3 cuentas)
python generate_accounts.py

# Generar 50 cuentas con 5 hilos
python generate_accounts.py -n 50 -t 5

# Establecer una contraseña específica para todas las cuentas
python generate_accounts.py -n 10 -p "MiContraseñaSecreta123!"
```

**Argumentos:**
*   `-n`, `--number`: Número de cuentas para crear (Por defecto: 3)
*   `-t`, `--threads`: Número de hilos concurrentes (1-8)
*   `-p`, `--password`: Contraseña común para todas las cuentas (Opcional)

#### Verificación Keep-Alive (Inicio de Sesión y Almacenamiento)
Para verificar todas las cuentas en `accounts.csv`, comprobar su cuota de almacenamiento y mantenerlas activas:

```bash
python signin_accounts.py
```

*   **No se requieren argumentos.**
*   Itera a través de todas las cuentas en `accounts.csv`.
*   **Omite cuentas marcadas como "Disabled".**
*   Actualiza el estado a `Active` o `Login Failed`.
*   Actualiza valores de almacenamiento usado/libre.


---

## :briefcase: Gestión Avanzada

### Exportando Datos
Puede exportar toda su base de datos de cuentas para copia de seguridad o uso externo.
1.  Haga clic en **Export** en la esquina superior derecha.
2.  Seleccione **Excel** para una hoja de cálculo formateada o **JSON** para datos sin procesar.
3.  Elija una ubicación para guardar.

*Las exportaciones en Excel incluyen columnas de estado codificadas por colores y encabezados formateados para facilitar la lectura.*

### Importando Datos
Migre desde versiones anteriores u otras herramientas.
1.  Haga clic en **Import**.
2.  Seleccione un archivo `.json` o `.xlsx` válido.
3.  La herramienta fusionará los datos en su `accounts.csv`.

---

## :grey_question: FAQ

<details>
<summary><strong>¿Por qué estoy limitado a 8 hilos?</strong></summary>
El proveedor de correo temporal (Mail.tm) tiene límites de tasa estrictos. Exceder 8 hilos concurrentes aumenta significativamente la probabilidad de prohibiciones de IP o fallos en la generación.
</details>

<details>
<summary><strong>¿Qué hace el botón "Sign In"?</strong></summary>
Realiza una verificación "Keep-Alive". Intenta iniciar sesión en sus cuentas usando `megatools`. Esto actualiza la información de cuota de almacenamiento y señala a MEGA que la cuenta está activa, evitando su eliminación.
</details>

<details>
<summary><strong>¿Dónde se guardan mis cuentas?</strong></summary>
Todos los datos se almacenan localmente en `accounts.csv` en el directorio de la aplicación. También puede exportar estos datos usando la función Exportar.
</details>

<details>
<summary><strong>Veo el error "Megatools not found".</strong></summary>
Si está ejecutando desde el código fuente, asegúrese de que `megatools` esté instalado y agregado a su PATH del Sistema. Si usa el ejecutable, esto se maneja automáticamente.
</details>

---

## :warning: Descargo de Responsabilidad

Esta herramienta se crea solo para **fines educativos y de prueba**. Usar este software para abusar de servicios de terceros, eludir restricciones o violar los términos de servicio (ToS) de MEGA.nz o Mail.tm está estrictamente prohibido. El desarrollador no asume responsabilidad por el mal uso.

---

## :sparkling_heart: Agradecimientos

*   Basado en el trabajo original de [f-o/MEGA-Account-Generator](https://github.com/f-o/MEGA-Account-Generator).
*   Componentes GUI por [TomSchimansky/CustomTkinter](https://github.com/TomSchimansky/CustomTkinter).
*   Mejorado y Mantenido por [byPancra](https://github.com/byPancra).

---

## :copyright: Licencia

Distribuido bajo la **Licencia MIT**. Vea [LICENSE](LICENSE) para detalles.

<div align="center">
  <sub>Desarrollado con ❤️ por <a href="https://github.com/byPancra">byPancra</a></sub>
</div>
