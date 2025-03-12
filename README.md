# atividade-ead-11-03
import java.util.Scanner;
public class Programa {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.println("Insira base!");
        double num = scanner.nextDouble();
        System.out.println("Insira altura!");
        double num1 = scanner.nextDouble();
        System.out.println("Insira largura!");
        double num2 = scanner.nextDouble();

        Calcular calcular = new Calcular(num1,num2,num);

        double area = Calcular.calcular_area(num,num1);
        double perimetro = Calcular.calcular_perimetro(num,num1);
        double diagonal = Calcular.calcular_diagonal(num,num1);


        System.out.println("AREA:" + area);
        System.out.println("PERIMETRO:" + perimetro);
        System.out.println("DIAGONAL:" + diagonal);

        scanner.close();
    }
}
public class Calcular {
    double num;
    double num1;
    double num2;
    double area;
    double perimetro;
    double diagonal;

    public static double calcular_area(double num, double num1) {

        return Math.sqrt(( num * num1));
    }

    public static double calcular_perimetro (double num, double num1) {

        return Math.sqrt(2 * (num + num1));

    }

    public static double calcular_diagonal (double num, double num1) {

        return Math.sqrt(Math.sqrt(Math.pow(num, 2) + Math.pow(num1, 2)));
    }
    public Calcular (double num, double num1, double num2){
        this.num = num;
        this.num1 = num1;
        this.num2 = num2;
    }


}
public class Principal {
    public static void main(String[] args) {
        
        Scanner scanner = new Scanner(System.in);

        
        System.out.print("Digite o nome do funcionário: ");
        String nome = scanner.nextLine();
        
        System.out.print("Digite o salário bruto do funcionário: ");
        double salarioBruto = scanner.nextDouble();
        
        System.out.print("Digite o valor do imposto: ");
        double imposto = scanner.nextDouble();

        
        Funcionario funcionario = new Funcionario(nome, salarioBruto, imposto);

        
        System.out.println("\nDados do Funcionário (Antes do Aumento):");
        System.out.println("Nome: " + funcionario.getNome());
        System.out.println("Salário Bruto: R$ " + funcionario.getSalarioBruto());
        System.out.println("Salário Líquido: R$ " + funcionario.calcularSalarioLiquido());

        
        System.out.print("\nDigite a porcentagem de aumento do salário: ");
        double percentualAumento = scanner.nextDouble();

        
        funcionario.aumentarSalario(percentualAumento);

       
        System.out.println("\nDados do Funcionário (Após o Aumento):");
        System.out.println("Nome: " + funcionario.getNome());
        System.out.println("Novo Salário Bruto: R$ " + funcionario.getSalarioBruto());
        System.out.println("Novo Salário Líquido: R$ " + funcionario.calcularSalarioLiquido());

        
        scanner.close();
    }
}
class Funcionario {
    private String nome;
    private double salarioBruto;
    private double imposto;

   
    public Funcionario(String nome, double salarioBruto, double imposto) {
        this.nome = nome;
        this.salarioBruto = salarioBruto;
        this.imposto = imposto;
    }

    
    public double calcularSalarioLiquido() {
        return salarioBruto - imposto;
    }

    
    public void aumentarSalario(double percentual) {
        double aumento = salarioBruto * percentual / 100;
        salarioBruto += aumento;
    }

    
    public String getNome() {
        return nome;
    }

    public double getSalarioBruto() {
        return salarioBruto;
    }

    public double getImposto() {
        return imposto;
    }
}
public class Main {
    public static void main(String[] args) {
        
        Scanner scanner = new Scanner(System.in);

       
        System.out.print("Digite o nome do aluno: ");
        String nome = scanner.nextLine();
        
        System.out.print("Digite a nota do 1º trimestre (vale 30): ");
        double nota1 = scanner.nextDouble();
        
        System.out.print("Digite a nota do 2º trimestre (vale 35): ");
        double nota2 = scanner.nextDouble();
        
        System.out.print("Digite a nota do 3º trimestre (vale 35): ");
        double nota3 = scanner.nextDouble();

        
        Student aluno = new Student(nome, nota1, nota2, nota3);

        
        double notaFinal = aluno.calcularNotaFinal();
        System.out.println("\nNota final de " + aluno.getNome() + ": " + notaFinal);

        
        String status = aluno.verificarStatus();
        System.out.println("Status: " + status);
        
        
        scanner.close();
    }
}
class Student {
    private String nome;
    private double nota1;
    private double nota2;
    private double nota3;

    
    public Student(String nome, double nota1, double nota2, double nota3) {
        this.nome = nome;
        this.nota1 = nota1;
        this.nota2 = nota2;
        this.nota3 = nota3;
    }

   
    public double calcularNotaFinal() {
        
        return (nota1 * 0.30) + (nota2 * 0.35) + (nota3 * 0.35);
    }

    
    public String verificarStatus() {
        double notaFinal = calcularNotaFinal();
        if (notaFinal >= 60) {
            return "PASS";
        } else {
            double pontosFaltando = 60 - notaFinal;
            return "FAILED - Faltam " + pontosFaltando + " pontos para aprovação.";
        }
    }

   
    public String getNome() {
        return nome;
    }

    public double getNota1() {
        return nota1;
    }

    public double getNota2() {
        return nota2;
    }

    public double getNota3() {
        return nota3;
    }
}
