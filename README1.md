<h1> Installation Instructions: </h1>


Install [Sagemath](https://www.sagemath.org/download-windows.html) on your computer. <br>
Install [Java](https://www.oracle.com/java/technologies/downloads/).

Write a simple Sage script that produces the desired output (https://doc.sagemath.org/html/en/reference/polynomial_rings/sage/rings/polynomial/polynomial_ring.html#sage.rings.polynomial.polynomial_ring.PolynomialRing_field.lagrange_polynomial):

``` p=11 ```
``` R.<x>=PolynomialRing(GF(p)) ```
``` points=[(1,1), (3,3)] ```
``` f=R.lagrange_polynomial(points) ```
``` print(f) ```

Save this code in the script **first.sage**. It can be executed from the command line using the command ```sage /path/to/myscript.sage```.

The goal is to use the numerical analysis features of Sage that are not implemented in Java. You will run a Sage script with the relevant function (Lagrange [interpolation]).

 public class ProcessOutputExample
 {
    public static void main(String[] arguments) throws IOException,InterruptedException {
        System.out.println(getProcessOutput());
    }

    public static String getProcessOutput() throws IOException, InterruptedException {
         ProcessBuilder processBuilder = new ProcessBuilder("sage", "first.sage");

         processBuilder.redirectErrorStream(true);

         Process process = processBuilder.start();
         StringBuilder processOutput = new StringBuilder();

         try (BufferedReader processOutputReader = new BufferedReader(new InputStreamReader(process.getInputStream()))) {
             String readLine;

             while ((readLine = processOutputReader.readLine()) != null)
                  processOutput.append(readLine + System.lineSeparator());
            process.waitFor();
         }

         return processOutput.toString().trim();
    }
 }

