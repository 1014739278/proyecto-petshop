import java.util.ArrayList;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.println("Ingrese nombre del perro:");
        String nombrePerro = sc.nextLine();
        System.out.println("Ingrese edad del perro:");
        int edadPerro = sc.nextInt();
        sc.nextLine();

        System.out.println("Ingrese nombre del gato:");
        String nombreGato = sc.nextLine();
        System.out.println("Ingrese edad del gato:");
        int edadGato = sc.nextInt();
        sc.nextLine();

        Perro perro1 = new Perro(nombrePerro, edadPerro);
        Gato gato1 = new Gato(nombreGato, edadGato);

        System.out.println("Ingrese nombre de producto 1:");
        String nombreProducto1 = sc.nextLine();
        System.out.println("Ingrese precio de producto 1:");
        double precioProducto1 = sc.nextDouble();
        sc.nextLine();

        System.out.println("Ingrese nombre de producto 2:");
        String nombreProducto2 = sc.nextLine();
        System.out.println("Ingrese precio de producto 2:");
        double precioProducto2 = sc.nextDouble();
        sc.nextLine();

        Producto producto1 = new Producto(nombreProducto1, precioProducto1);
        Producto producto2 = new Producto(nombreProducto2, precioProducto2);

        Tienda tienda = new Tienda();
        tienda.agregarAnimal(perro1);
        tienda.agregarAnimal(gato1);
        tienda.agregarProducto(producto1);
        tienda.agregarProducto(producto2);

        System.out.println("Ingrese nombre del cliente:");
        String nombreCliente = sc.nextLine();
        Cliente cliente1 = new Cliente(nombreCliente, gato1);

        tienda.mostrarInventario();
        System.out.println("\n=== Información del cliente ===");
        cliente1.mostrarCliente();

        sc.close();
    }
}

class Animal {
    private String nombre;
    private int edad;

    public Animal(String nombre, int edad) {
        this.nombre = nombre;
        this.edad = edad;
    }

    public void hacerSonido() {
        System.out.println("Este animal hace un sonido.");
    }

    public String getNombre() {
        return nombre;
    }

    public int getEdad() {
        return edad;
    }
}

class Perro extends Animal {
    public Perro(String nombre, int edad) {
        super(nombre, edad);
    }

    @Override
    public void hacerSonido() {
        System.out.println(getNombre() + " dice: ¡Guau guau!");
    }
}

class Gato extends Animal {
    public Gato(String nombre, int edad) {
        super(nombre, edad);
    }

    @Override
    public void hacerSonido() {
        System.out.println(getNombre() + " dice: ¡Miau miau!");
    }
}

class Producto {
    private String nombre;
    private double precio;

    public Producto(String nombre, double precio) {
        this.nombre = nombre;
        this.precio = precio;
    }

    public String getInfo() {
        return "Producto: " + nombre + ", Precio: $" + precio;
    }
}

class Cliente {
    private String nombre;
    private Animal mascota;

    public Cliente(String nombre, Animal mascota) {
        this.nombre = nombre;
        this.mascota = mascota;
    }

    public void mostrarCliente() {
        System.out.println("Cliente: " + nombre);
        mascota.hacerSonido();
    }
}

class Tienda {
    private ArrayList<Animal> animales;
    private ArrayList<Producto> productos;

    public Tienda() {
        animales = new ArrayList<>();
        productos = new ArrayList<>();
    }

    public void agregarAnimal(Animal a) {
        animales.add(a);
    }

    public void agregarProducto(Producto p) {
        productos.add(p);
    }

    public void mostrarInventario() {
        System.out.println("=== Animales en la tienda ===");
        for (Animal a : animales) {
            System.out.println("Nombre: " + a.getNombre() + ", Edad: " + a.getEdad());
            a.hacerSonido();
        }

        System.out.println("\n=== Productos en la tienda ===");
        for (Producto p : productos) {
            System.out.println(p.getInfo());
        }
    }
}
