public class Main {
    public static void main(String[] args) {
        ListaEnlazada lista = new ListaEnlazada();

        // Usamos tu DPI: 3115765240805
        int[] valores = {3, 1, 1, 5, 7, 6, 5, 2, 4, 0, 8, 0, 5};

        System.out.println("Insertando valores:");
        for (int valor : valores) {
            lista.agregarAlFinal(valor);
        }

        lista.mostrarLista();

        System.out.println("\nEliminando el número 5:");
        lista.eliminar(5);
        lista.mostrarLista();

        System.out.println("\nVaciando la lista:");
        lista.vaciar();
        lista.mostrarLista();
    }
}

// Clase Nodo
class Nodo {
    int dato;
    Nodo siguiente;

    public Nodo(int dato) {
        this.dato = dato;
        this.siguiente = null;
    }
}

// Clase ListaEnlazada
class ListaEnlazada {
    Nodo cabeza;

    public ListaEnlazada() {
        cabeza = null;
    }

    public void agregarAlFinal(int dato) {
        Nodo nuevo = new Nodo(dato);
        if (cabeza == null) {
            cabeza = nuevo;
        } else {
            Nodo actual = cabeza;
            while (actual.siguiente != null) {
                actual = actual.siguiente;
            }
            actual.siguiente = nuevo;
        }
    }

    public void eliminar(int valor) {
        if (cabeza == null) return;

        if (cabeza.dato == valor) {
            cabeza = cabeza.siguiente;
            return;
        }

        Nodo actual = cabeza;
        while (actual.siguiente != null && actual.siguiente.dato != valor) {
            actual = actual.siguiente;
        }

        if (actual.siguiente != null) {
            actual.siguiente = actual.siguiente.siguiente;
        }
    }

    public void mostrarLista() {
        Nodo actual = cabeza;
        while (actual != null) {
            System.out.print(actual.dato + " -> ");
            actual = actual.siguiente;
        }
        System.out.println("null");
    }

    public void vaciar() {
        cabeza = null;
    }
}
