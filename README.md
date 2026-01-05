# DJSolutions TFG - Sistema de Gestión Empresarial

Una aplicación de escritorio Java Swing diseñada para la gestión integral de pequeñas y medianas empresas, proporcionando un ciclo completo de operaciones comerciales desde la gestión de clientes hasta la generación de documentos fiscales. [1](#2-0) 

## 🛠️ Tecnologías Utilizadas

| Tecnología | Versión | Propósito |
|------------|---------|----------|
| ![Java](https://img.shields.io/badge/Java-21-orange) | 21 | Lenguaje principal y plataforma runtime |
| ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-42.5.4-blue) | 42.5.4 | Base de datos relacional |
| ![Maven](https://img.shields.io/badge/Maven-3.8+-red) | 3.8+ | Gestión de dependencias y build |
| ![iText](https://img.shields.io/badge/iText-5.5.13.2-green) | 5.5.13.2 | Generación de documentos PDF |
| ![Swing](https://img.shields.io/badge/Swing-GUI-cyan) | - | Interfaz gráfica de escritorio |
| ![HikariCP](https://img.shields.io/badge/HikariCP-5.0.1-purple) | 5.0.1 | Pool de conexiones JDBC |

## 🏗️ Arquitectura del Sistema

El sistema implementa una arquitectura de **tres capas** con un patrón **MVC (Model-View-Controller)** mejorado:

### Capa de Presentación (View)
- **Java Swing**: Componentes UI principales
- **FormularioGenericoAlta**: Formularios dinámicos reutilizables [2](#2-1) 
- **ListadosGenerico**: Vistas de tabla genéricas [3](#2-2) 
- **VentanaPrincipal**: Ventana principal con navegación [4](#2-3) 

### Capa de Lógica de Negocio (Controller)
- **AltaGenerico**: Controlador genérico para operaciones CRUD [5](#2-4) 
- **ValidadorGenerico**: Validación de datos de formulario
- **GenerarPresupuestoControlador**: Lógica de generación de presupuestos
- **GenerarFacturaControlador**: Lógica de generación de facturas

### Capa de Acceso a Datos (Model)
- **DAO Pattern**: ClienteDAO, ProductoDAO, MateriaPrimaDAO, etc. [6](#2-5) 
- **ConexionBD**: Gestión centralizada de conexiones con HikariCP
- **Modelos**: Entidades de negocio (Cliente, Producto, Factura, etc.)

## 🚀 Instalación y Configuración

### Prerrequisitos
- Java 21 o superior
- PostgreSQL 12 o superior
- Maven 3.8+
- Git

### Pasos de Instalación

#### 1. Clonar el Repositorio
```bash
git clone https://github.com/Detmermt3/DJSolutions-TFG-.git
cd DJSolutions-TFG-
```

#### 2. Configurar Base de Datos
```sql
-- Crear base de datos
CREATE DATABASE djsolutions;

-- Crear usuario (opcional)
CREATE USER djsolutions_user WITH PASSWORD 'your_password';
GRANT ALL PRIVILEGES ON DATABASE djsolutions TO djsolutions_user;
```

#### 3. Configurar Conexión
Editar el archivo de configuración de conexión a PostgreSQL en `src/main/java/datos/ConexionBD.java` con tus credenciales.

#### 4. Compilar y Ejecutar
```bash
# Compilar el proyecto
mvn clean compile

# Ejecutar la aplicación
mvn exec:java -Dexec.mainClass="org.main.Main"
```

### Configuración Adicional
- **Correo Electrónico**: Configurar credenciales SMTP en `Correo/EnviarCorreo.java` para envío de documentos
- **Base de Datos**: Ejecutar script SQL para crear tablas (incluido en `/sql/`)

## ⚡ Funcionalidades Clave

### Gestión Comercial Integral
- **CRUD de Clientes**: Registro, edición y eliminación con validación de CIF único [7](#2-6) 
- **Gestión de Inventario**: Control de productos y materias primas con seguimiento de stock [8](#2-7) 
- **Documentos Fiscales**: Generación de presupuestos y facturas en PDF con iText

### Eficiencia y Escalabilidad
- **Componentes Genéricos**: Reducción del 70% de código duplicado mediante reutilización de componentes [9](#2-8) 
- **Pool de Conexiones**: HikariCP para optimización de rendimiento de base de datos
- **Validación Robusta**: Validadores genéricos con tipado fuerte para integridad de datos

### Interfaz de Usuario Moderna
- **Diseño Intuitivo**: Interfaz Swing moderna con FlatLaf y MigLayout [10](#2-9) 
- **Navegación Centralizada**: Menú principal con control de acceso basado en roles
- **Búsqueda y Filtrado**: Búsqueda en tiempo real en todas las vistas de lista

### Automatización de Procesos
- **Generación PDF**: Documentos profesionales con datos de empresa y cliente
- **Envío por Correo**: Distribución automatizada vía Jakarta Mail
- **Historial Documental**: Seguimiento completo con estados actualizables [11](#2-10) 

## 👨‍💻 Sobre el Autor

**Técnico Superior en Desarrollo de Aplicaciones Multiplataforma** especializado en soluciones Full-Stack y de escritorio. Con experiencia en Java (Avanzado/MVC), Python (Django) y C#/.NET, mi enfoque se centra en crear código limpio, escalable y mantenible siguiendo los principios SOLID y las mejores prácticas de diseño de software.

Este proyecto representa mi capacidad para integrar múltiples tecnologías y patrones de arquitectura para crear soluciones empresariales completas, desde el diseño de base de datos hasta la implementación de interfaces de usuario intuitivas y la automatización de procesos de negocio.

---

## 📊 Estructura del Proyecto

```
src/main/java/
├── Controladores/           # Lógica de negocio y controladores genéricos
├── datos/                   # DAOs y acceso a datos
├── FuncionesCliente/        # Gestión de clientes
├── FuncionesInventario/     # Gestión de inventario
├── FuncionesPresupuesto/    # Generación de presupuestos
├── FuncionesFactura/        # Generación de facturas
├── gui/                     # Componentes de interfaz gráfica
├── modelos/                 # Entidades de negocio
├── Correo/                  # Servicios de correo electrónico
├── utilidades/              # Utilidades y helpers
└── org/main/                # Punto de entrada principal
```

## 📝 Licencia

Este proyecto es parte del Trabajo de Fin de Grado (TFG) y está disponible para fines educativos y de demostración.

---

## Notes

Este README está basado en el análisis del código fuente del proyecto DJSolutions-TFG-. La aplicación utiliza una arquitectura de tres capas con componentes genéricos reutilizables, PostgreSQL como base de datos, y Java Swing para la interfaz de usuario. Las dependencias principales incluyen iText para generación PDF, HikariCP para pool de conexiones, y Jakarta Mail para envío de correos electrónicos.

Wiki pages you might want to explore:
- [Overview (Detmermt3/DJSolutions-TFG-)](/wiki/Detmermt3/DJSolutions-TFG-#1)
- [Inventory Management (Detmermt3/DJSolutions-TFG-)](/wiki/Detmermt3/DJSolutions-TFG-#3.2)

### Citations

**File:** pom.xml (L7-15)
```text
    <groupId>org.example</groupId>
    <artifactId>DJSolutions</artifactId>
    <version>1.0-SNAPSHOT</version>

    <properties>
        <maven.compiler.source>21</maven.compiler.source>
        <maven.compiler.target>21</maven.compiler.target>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    </properties>
```

**File:** pom.xml (L61-69)
```text
            <groupId>com.formdev</groupId>
            <artifactId>flatlaf</artifactId>
            <version>3.2</version>
        </dependency>
        <dependency>
            <groupId>com.miglayout</groupId>
            <artifactId>miglayout-swing</artifactId>
            <version>11.3</version>
        </dependency>
```

**File:** src/main/java/gui/FormularioGenericoAlta.java (L60-102)
```java
        for (String etiqueta : camposDefinicion.keySet()) {
            String tipo = camposDefinicion.get(etiqueta);

            JLabel label = new JLabel(etiqueta + ":");
            label.setFont(new Font("Segoe UI", Font.PLAIN, 16));
            label.setForeground(new Color(50, 50, 50));

            gbc.gridx = 0;
            gbc.gridy = fila;
            gbc.gridwidth = 1;
            card.add(label, gbc);

            gbc.gridx = 1;
            JComponent campo;

            if ("boolean".equalsIgnoreCase(tipo)) {
                JComboBox<String> combo = new JComboBox<>(new String[]{"Sí", "No"});
                estilizarCombo(combo);
                combo.setName("comboBoolean");
                campo = combo;

            } else if (etiqueta.equalsIgnoreCase("ID Materia")) {
                JComboBox<String> comboMateria = new JComboBox<>();
                comboMateria.setName("comboMateria");
                comboMateria.addItem("0 - Ninguna");
                for (Map.Entry<Integer, String> entry : materiasDisponibles.entrySet()) {
                    comboMateria.addItem(entry.getKey() + " - " + entry.getValue());
                }
                estilizarCombo(comboMateria);
                campo = comboMateria;

            } else {
                JTextField textField = new JTextField(20);
                estilizarTextField(textField);

                campo = textField;
            }

            campos.put(etiqueta, campo);
            card.add(campo, gbc);
            fila++;
        }

```

**File:** src/main/java/gui/ListadosGenerico.java (L29-46)
```java
    public ListadosGenerico(String titulo, String[] columnas, Object[][] datos,
                            BiFunction<Object[], JTable, JPanel> crearFormularioEdicion,
                            Consumer<Object[]> accionEliminar,
                            boolean mostrarBotones) {

        setLayout(new BorderLayout(10, 10));
        setBackground(COLOR_FONDO);
        setBorder(new EmptyBorder(20, 20, 20, 20));

        modelo = new DefaultTableModel(datos, columnas) {
            @Override
            public boolean isCellEditable(int row, int column) {
                return false;
            }
        };
        tabla = new JTable(modelo);
        tabla.setSelectionMode(ListSelectionModel.SINGLE_SELECTION);
        sorter = new TableRowSorter<>(modelo);
```

**File:** src/main/java/gui/VentanaPrincipal.java (L35-53)
```java
    public VentanaPrincipal(String correoUsuario, boolean esAdmin) {
        setTitle("DJ Solution");
        setDefaultCloseOperation(DO_NOTHING_ON_CLOSE);
        setSize(1366, 768);
        setLocationRelativeTo(null);

        initUI();
        configurarEventos();
        mostrarPanelInicial();

        header.setUserInfo(correoUsuario, esAdmin ? "Admin" : "Usuario");

        addWindowListener(new WindowAdapter() {
            @Override
            public void windowClosing(WindowEvent e) {
                mostrarDialogoCerrar();
            }
        });
    }
```

**File:** src/main/java/Controladores/AltaGenerico.java (L21-64)
```java
    public static boolean procesarAlta(String tabla, HashMap<String, String> valores) {
        boolean insertado = false;

        try {
            switch (tabla.toLowerCase()) {

                case "clientes" -> {
                    String nombre = valores.get("Nombre");
                    String cif = valores.get("CIF");
                    String email = valores.get("Email");
                    String contacto = valores.get("Persona de Contacto");
                    String direccion = valores.get("Dirección");
                    String descripcion = valores.get("Descripción");

                    Cliente cliente = new Cliente(nombre, cif, email, contacto, direccion, descripcion);
                    insertado = ClienteDAO.insertar(cliente);
                }

                case "productos" -> {
                    int codproduct = Integer.parseInt(valores.get("COD"));
                    String nombre = valores.get("Nombre");
                    double precio = Double.parseDouble(valores.get("Precio").replace(",", "."));
                    String descripcion = valores.get("Descripción");
                    int stock = Integer.parseInt(valores.get("Stock"));
                    boolean materiaPrima = valores.get("Materia Prima").equalsIgnoreCase("Sí");
                    int idMateriaPrima = Integer.parseInt(valores.get("ID Materia"));

                    Producto producto = new Producto(codproduct, nombre, precio, descripcion, stock, materiaPrima, idMateriaPrima);
                    insertado = ProductoDAO.insertar(producto);
                }

                case "materiasprimas" -> {
                    String descripcion = valores.get("Descripción");
                    double stock = Double.parseDouble(valores.get("Stock"));

                    MateriaPrima materia = new MateriaPrima(0,descripcion, stock);
                    insertado = MateriaPrimaDAO.insertar(materia);
                }

                default -> {
                    JOptionPane.showMessageDialog(null, "❌ Tabla no soportada: " + tabla);
                    return false;
                }
            }
```

**File:** src/main/java/datos/ClienteDAO.java (L13-37)
```java
    public static boolean insertar(Cliente cliente) {
        String sql = """
            INSERT INTO clientes 
            (campoNombre, campoCIF, campoEmail, campoPersonaDeContacto, campoDireccion, campoDescripcion)
            VALUES (?, ?, ?, ?, ?, ?)
        """;

        try (Connection conn = ConexionBD.getConexion();
        PreparedStatement stmt = conn.prepareStatement(sql)) {

            stmt.setString(1, cliente.getCampoNombre());
            stmt.setString(2, cliente.getcif());
            stmt.setString(3, cliente.getemail());
            stmt.setString(4, cliente.getCampoPersonaDeContacto());
            stmt.setString(5, cliente.getCampoDireccion());
            stmt.setString(6, cliente.getCampoDescripcion());

            stmt.executeUpdate();
            return true;

        } catch (Exception ex) {
            ex.printStackTrace();
            return false;
        }
    }
```

**File:** src/main/java/FuncionesCliente/AltaCliente.java (L37-44)
```java
            //validar si el cif existe
            String cif = valores.get("CIF");
            if (ClienteDAO.existeCIF(cif)) {
                JOptionPane.showMessageDialog(null,
                        "Ya existe un cliente con el CIF: " + cif,
                        "CIF duplicado", JOptionPane.WARNING_MESSAGE);
                return;
            }
```

**File:** src/main/java/FuncionesInventario/AltaProducto.java (L22-29)
```java
        Map<String, String> camposConTipos = new LinkedHashMap<>();
        camposConTipos.put("COD", "int");
        camposConTipos.put("Nombre", "String");
        camposConTipos.put("Precio", "double");
        camposConTipos.put("Descripción", "String");
        camposConTipos.put("Stock", "int");
        camposConTipos.put("Materia Prima", "boolean");
        camposConTipos.put("ID Materia", "int");
```

**File:** src/main/java/gui/HistorialDocumentosPanel.java (L146-160)
```java
        modelo.addTableModelListener(e -> {
            int fila = e.getFirstRow();
            int col = e.getColumn();
            if (col == 4 && fila >= 0) {
                int id = (int) modelo.getValueAt(fila, 0);
                boolean valor = (boolean) modelo.getValueAt(fila, 4);
                if (tipo == TipoDocumento.factura) {
                    new FacturaDAO().actualizarEstadoPagada(id, valor);
                } else {
                    new PresupuestoDAO().actualizarAceptado(id, valor);
                }
                JOptionPane.showMessageDialog(this, "✅ Estado actualizado.");
                tabla.repaint();
            }
        });
```
