/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 * Click nbfs://nbhost/SystemFileSystem/Templates/Classes/Class.java to edit this template
 */
package com.mycompany.ado1e;

/**
 *
 * @author alessandro.rmsilva
 */
import java.util.Arrays;
import java.util.Random;
import java.util.String;

public class Livro {
    private int id;
    private String autor;
    private String titulo;
    private double preco;

    public Livro(String autor, String titulo, double preco) {
        this.id = gerarId();
        this.autor = autor;
        this.titulo = titulo;
        this.preco = preco;
    }

    private int gerarId() {
        Random rand = new Random();
        return rand.nextInt(1000);
    }

    public int getId() {
        return id;
    }

    public String getAutor() {
        return autor;
    }

    public void setAutor(String autor) {
        this.autor = autor;
    }

    public String getTitulo() {
        return titulo;
    }

    public void setTitulo(String titulo) {
        this.titulo = titulo;
    }

    public double getPreco() {
        return preco;
    }

    public void setPreco(double preco) {
        this.preco = preco;
    }

    @Override
    public String toString() {
        return "Livro [id=" + id + ", autor=" + autor + ", titulo=" + titulo + ", preco=" + preco + "]";
    }
}

public class Biblioteca {
    private Livro[] livros;

    public Biblioteca() {
        this.livros = new Livro[0];
    }

    public void inserirLivro(Livro livro) {
        livros = Arrays.copyOf(livros, livros.length + 1);
        livros[livros.length - 1] = livro;
    }

    public void removerLivro(int id) {
        for (int i = 0; i < livros.length; i++) {
            if (livros[i].getId() == id) {
                livros = removerElemento(livros, i);
                break;
            }
        }
    }

    private Livro[] removerElemento(Livro[] array, int index) {
        Livro[] novoArray = new Livro[array.length - 1];
        int j = 0;

        for (int i = 0; i < array.length; i++) {
            if (i != index) {
                novoArray[j] = array[i];
                j++;
            }
        }

        return novoArray;
    }

    public void ordenarLivros() {
        Arrays.sort(livros, (a, b) -> a.getTitulo().compareTo(b.getTitulo()));
    }

    public Livro[] buscarLivro(String titulo) {
        Livro[] resultado = new Livro[0];

        for (Livro livro : livros) {
            if (livro.getTitulo().equals(titulo)) {
                resultado = Arrays.copyOf(resultado, resultado.length + 1);
                resultado[resultado.length - 1] = livro;
            }
        }

        return resultado;
    }
}
