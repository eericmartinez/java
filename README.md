se# java
java repositorie


import java.io.IOException;
import java.nio.file.*;
import java.util.*;
import java.util.regex.*;

public class AnnotationCounter {
    public static void main(String[] args) {
        String projectPath = "ruta/a/tu/proyecto"; // Cambia a la ruta de tu proyecto
        Map<String, Integer> annotationCount = new HashMap<>();

        try {
            // Recorremos todos los archivos del proyecto
            Files.walk(Paths.get(projectPath))
                .filter(Files::isRegularFile)
                .filter(file -> file.toString().endsWith(".java"))
                .forEach(file -> processFile(file, annotationCount));

            // Mostramos el resultado
            System.out.println("Conteo de anotaciones:");
            annotationCount.forEach((annotation, count) -> 
                System.out.println(annotation + ": " + count));

        } catch (IOException e) {
            e.printStackTrace();
        }
    }

    private static void processFile(Path file, Map<String, Integer> annotationCount) {
        try {
            List<String> lines = Files.readAllLines(file);
            Pattern annotationPattern = Pattern.compile("@\\w+");

            for (String line : lines) {
                Matcher matcher = annotationPattern.matcher(line);
                while (matcher.find()) {
                    String annotation = matcher.group();
                    annotationCount.put(annotation, annotationC
                    
                    ount.getOrDefault(annotation, 0) + 1);
                }import java.io.IOException;
import java.nio.file.*;
import java.util.*;
import java.util.regex.*;

public class AnnotationCounter {
    public static void main(String[] args) {
        String projectPath = "ruta/a/tu/proyecto"; // Cambia a la ruta de tu proyecto
        Map<String, Integer> annotationCount = new HashMap<>();

        try {
            // Recorremos todos los archivos del proyecto
            Files.walk(Paths.get(projectPath))
                .filter(Files::isRegularFile)
                .filter(file -> file.toString().endsWith(".java"))
                .forEach(file -> processFile(file, annotationCount));

            // Mostramos el resultado
            System.out.println("Conteo de anotaciones:");
            annotationCount.forEach((annotation, count) -> 
                System.out.println(annotation + ": " + count));

        } catch (IOException e) {
            e.printStackTrace();
        }
    }

    private static void processFile(Path file, Map<String, Integer> annotationCount) {
        try {
            List<String> lines = Files.readAllLines(file);
            Pattern annotationPattern = Pattern.compile("@\\w+");

            for (String line : lines) {
                Matcher matcher = annotationPattern.matcher(line);
                while (matcher.find()) {
                    String annotation = matcher.group();
                    annotationCount.put(annotation, annotationCount.getOrDefault(annotation, 0) + 1);
                }
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}





import java.io.IOException;
import java.nio.file.*;
import java.util.*;

public class ProjectAnalyzer {
    public static void main(String[] args) {
        String projectPath = "ruta/a/tu/proyecto"; // Cambia a la ruta de tu proyecto
        Map<String, Integer> projectCount = new HashMap<>();

        try {
            Files.walk(Paths.get(projectPath))
                .filter(Files::isRegularFile)
                .forEach(file -> classifyFile(file, projectCount));

            // Mostramos el conteo de subproyectos detectados
            System.out.println("Subproyectos detectados:");
            projectCount.forEach((projectType, count) -> 
                System.out.println(projectType + ": " + count));

        } catch (IOException e) {
            e.printStackTrace();
        }
    }

    private static void classifyFile(Path file, Map<String, Integer> projectCount) {
        String fileName = file.getFileName().toString();

        if (fileName.equals("pom.xml")) {
            projectCount.put("Maven", projectCount.getOrDefault("Maven", 0) + 1);
        } else if (fileName.equals("build.gradle") || fileName.equals("settings.gradle")) {
            projectCount.put("Gradle", projectCount.getOrDefault("Gradle", 0) + 1);
        } else if (fileName.equals("ivy.xml")) {
            projectCount.put("Ivy", projectCount.getOrDefault("Ivy", 0) + 1);
        }
    }
}






import java.io.IOException;
import java.nio.file.*;
import java.util.*;

public class ProjectAnalyzer {
    public static void main(String[] args) {
        String projectPath = "ruta/a/tu/proyecto"; // Cambia a la ruta de tu proyecto
        Map<String, Integer> projectCount = new HashMap<>();

        try {
            Files.walk(Paths.get(projectPath))
                .filter(Files::isRegularFile)
                .forEach(file -> classifyFile(file, projectCount));

            // Mostramos el conteo de subproyectos detectados
            System.out.println("Subproyectos detectados:");
            projectCount.forEach((projectType, count) -> 
                System.out.println(projectType + ": " + count));

        } catch (IOException e) {
            e.printStackTrace();
        }
    }

    private static void classifyFile(Path file, Map<String, Integer> projectCount) {
        String fileName = file.getFileName().toString();

        if (fileName.equals("pom.xml")) {
            projectCount.put("Maven", projectCount.getOrDefault("Maven", 0) + 1);
        } else if (fileName.equals("build.gradle") || fileName.equals("settings.gradle")) {
            projectCount.put("Gradle", projectCount.getOrDefault("Gradle", 0) + 1);
        } else if (fileName.equals("ivy.xml")) {
            projectCount.put("Ivy", projectCount.getOrDefault("Ivy", 0) + 1);
        }
    }
}
import java.io.IOException;
import java.nio.file.*;
import java.util.*;

public class ProjectAnalyzer {
    public static void main(String[] args) {
        String projectPath = "ruta/a/tu/proyecto"; // Cambia a la ruta de tu proyecto
        Map<String, Integer> projectCount = new HashMap<>();

        try {
            Files.walk(Paths.get(projectPath))
                .filter(Files::isRegularFile)
                .forEach(file -> classifyFile(file, projectCount));

            // Mostramos el conteo de subproyectos detectados
            System.out.println("Subproyectos detectados:");
            projectCount.forEach((projectType, count) -> 
                System.out.println(projectType + ": " + count));

        } catch (IOException e) {
            e.printStackTrace();
        }
    }

    private static void classifyFile(Path file, Map<String, Integer> projectCount) {
        String fileName = file.getFileName().toString();

        if (fileName.equals("pom.xml")) {
            projectCount.put("Maven", projectCount.getOrDefault("Maven", 0) + 1);
        } else if (fileName.equals("build.gradle") || fileName.equals("settings.gradle")) {
            projectCount.put("Gradle", projectCount.getOrDefault("Gradle", 0) + 1);
        } else if (fileName.equals("ivy.xml")) {
            projectCount.put("Ivy", projectCount.getOrDefault("Ivy", 0) + 1);
        }
    }
}





import java.io.IOException;
import java.nio.file.*;
import java.util.*;

public class ProjectRestructurer {
    public static void main(String[] args) {
        String projectPath = "ruta/a/tu/proyecto"; // Cambia a la ruta de tu proyecto base
        Map<String, List<String>> suggestedStructure = new HashMap<>();

        try {
            Files.walk(Paths.get(projectPath))
                .filter(Files::isRegularFile)
                .forEach(file -> analyzeFile(file, suggestedStructure));

            // Mostrar la sugerencia de reestructuración
            System.out.println("Sugerencia de reestructuración del proyecto:");
            suggestedStructure.forEach((projectType, files) -> {
                System.out.println("Proyecto de tipo " + projectTyp              
                e + ":");
                files.forEach(file -> System.out.println("  - " + file));
            });

        } catch (IOException e) {
            e.printStackTrace();
        }
    }

    private static void analyzeFile(Path file, Map<String, List<String>> suggestedStructure) {
        String fileName = file.getFileName().toString();
        String parentDir = file.getParent().toString(); //







            }
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}




reorganizaimport java.io.IOException;
import java.nio.file.*;
import java.util.*;

public class ProjectRestructurer {
    public static void main(String[] args) {
        String projectPath = "ruta/a/tu/proyecto"; // Cambia a la ruta de tu proyecto base
        Map<String, List<String>> suggestedStructure = new HashMap<>();

        try {
            Files.walk(Paths.get(projectPath))
                .filter(Files::isRegularFile)
                .forEach(file -> analyzeFile(file, suggestedStructure));

            // Mostrar la sugerencia de reestructuración
            System.out.println("Sugerencia de reestructuración del proyecto:");
            suggestedStructure.forEach((projectType, files) -> {
                System.out.println("Proyecto de tipo " + projectType + ":");
                files.forEach(file -> System.out.println("  - " + file));
            });

        } catch (IOException e) {
            e.printStackTrace();
        }
    }

    private static void analyzeFile(Path file, Map<String, List<String>> suggestedStructure) {
        String fileName = file.getFileName().toString();
        String parentDir = file.getParent().toString(); // Obtener el directorio del archivo

        if (fileName.equals("pom.xml")) {
            addToStructure(suggestedStructure, "Maven", parentDir);
        } else if (fileName.equals("build.gradle") || fileName.equals("settings.gradle")) {
            addToStructure(suggestedStructure, "Gradle", parentDir);
        } else if (fileName.equals("ivy.xml")) {
            addToStructure(suggestedStructure, "Ivy", parentDir);
        }
    }

    private static void addToStructure(Map<String, List<String>> structure, String projectType, String directory) {
        // Agrega el directorio al tipo de proyecto correspondiente
        structure.putIfAbsent(projectType, new ArrayList<>());
        if (!structure.get(projectType).contains(directory)) {
            structure.get(projectType).add(directory);
        }
    }
}




import java.io.File;
import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Path;
import java.nio.file.Paths;
import java.util.ArrayList;
import java.util.List;
import java.util.regex.Matcher;
import java.util.regex.Pattern;

public class CodeAnalyzer {

    private static final String PROJECT_PATH = "ruta/del/proyecto"; // Cambia esto a la ruta de tu proyecto
    
    // Expresiones regulares para detectar referencias a EJB y anotaciones de Spring Boot
    private static final Pattern EJB_PATTERN = Pattern.compile("\\b(EJB|@EJB|@Stateless|@Stateful)\\b");
    private static final Pattern SPRING_ANNOTATIONS_PATTERN = Pattern.compile(
        "\\b(@Controller|@Service|@Component|@Repository)\\b"
    );

    public static void main(String[] args) {
        List<String> ejbClasses = new ArrayList<>();
        List<String> springClasses = new ArrayList<>();
        
        // Analiza los archivos Java en el proyecto
        analyzeProject(new File(PROJECT_PATH), ejbClasses, springClasses);
        
        // Imprime los resultados
        System.out.println("Clases con referencias a EJB:");
        ejbClasses.forEach(System.out::println);

        System.out.println("\nClases con anotaciones de Spring Boot:");
        springClasses.forEach(System.out::println);
    }

    private static void analyzeProject(File folder, List<String> ejbClasses, List<String> springClasses) {
        for (File file : folder.listFiles()) {
            if (file.isDirectory()) {
                // Analiza recursivamente si es una carpeta
                analyzeProject(file, ejbClasses, springClasses);
            } else if (file.getName().endsWith(".java")) {
                // Analiza el archivo Java
                analyzeFile(file.toPath(), ejbClasses, springClasses);
            }
        }
    }

    private static void analyzeFile(Path filePath, List<String> ejbClasses, List<String> springClasses) {
        try {
            List<String> lines = Files.readAllLines(filePath);
            String content = String.join(" ", lines);
            
            // Busca referencias a EJB
            Matcher ejbMatcher = EJB_PATTERN.matcher(content);
            if (ejbMatcher.find()) {
                ejbClasses.add(filePath.toString());
            }
            
            // Busca anotaciones de Spring Boot
            Matcher springMatcher = SPRING_ANNOTATIONS_PATTERN.matcher(content);
            if (springMatcher.find()) {
                springClasses.add(filePath.toString());
            }
        } catch (IOException e) {
            System.err.println("Error leyendo el archivo: " + filePath + " - " + e.getMessage());
        }
    }
}




import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        String cadena = "1234"; // Cambia esta cadena de prueba según necesites

        // Validamos si la cadena es numérica y tiene menos de 10 caracteres, si es así, la rellenamos
        cadena = validarYRellenarConCeros(cadena);

        System.out.println("Cadena final: " + cadena);
    }

    // Método que valida si es numérica y rellena con ceros si cumple con la longitud
    public static String validarYRellenarConCeros(String cadena) {
        if (cadena.length() < 10 && esNumerica(cadena)) {
            return String.format("%-10s", cadena).replace(' ', '0'); // Rellenamos con ceros hasta alcanzar 10 caracteres
        }
        return cadena;
    }

    // Método que verifica si la cadena es numérica (sin expresiones regulares)
    public static boolean esNumerica(String cadena) {
        for (char c : cadena.toCharArray()) {
            if (!Character.isDigit(c)) {
                return false; // Si algún carácter no es un dígito, retorna false
            }
        }
        return true; // Si todos son dígitos, retorna true
    }
}

public class Main {
    public static void main(String[] args) {
        String cadena = "123 456"; // Cambia esta cadena de prueba según necesites

        try {
            // Limpiamos espacios en blanco
            cadena = eliminarEspacios(cadena);
            // Validamos que sea numérica
            validarCadenaNumerica(cadena);
            
            System.out.println("Cadena válida: " + cadena);
        } catch (InvalidStringException e) {
            System.out.println("Error: " + e.getMessage());
        }
    }

    // Método para eliminar espacios en blanco de la cadena
    public static String eliminarEspacios(String cadena) {
        return cadena.replace(" ", "");
    }

    // Método para validar que la cadena sea numérica
    public static void validarCadenaNumerica(String cadena) throws InvalidStringException {
        if (!cadena.matches("^[0-9]+$")) {
            throw new InvalidStringException("La cadena contiene caracteres no numéricos.");
        }
    }
}

// Excepción personalizada
class InvalidStringException extends Exception {
    public InvalidStringException(String mensaje) {
        super(mensaje);
    }
}


# 1. Instalar Git si aún no lo tienes instalado
# Para Ubuntu/Debian:
sudo apt-get install git

# Para macOS (usando Homebrew):
brew install git

# Para Windows: Descarga el instalador de https://git-scm.com/download/win

# 2. Configurar tu información de usuario en Git
git config --global user.name "Tu Nombre"
git config --global user.email "tu.email@ejemplo.com"

# 3. Generar una clave SSH (si planeas usar SSH en lugar de HTTPS)
ssh-keygen -t ed25519 -C "tu.email@ejemplo.com"

# 4. Clonar un repositorio existente
git clone https://github.com/usuario/repositorio.git

# O si usas SSH:
git clone git@github.com:usuario/repositorio.git

# 5. Si estás iniciando un nuevo repositorio local:
mkdir mi-proyecto
cd mi-proyecto
git init
git add .
git commit -m "Commit inicial"

# 6. Conectar con repositorio remoto (si iniciaste local)
git remote add origin https://github.com/usuario/repositorio.git

# 7. Subir cambios al repositorio remoto
git push -u origin main  # o 'master' en repositorios más antiguos


<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>3.2.0</version>
        <relativePath/>
    </parent>
    
    <groupId>com.example</groupId>
    <artifactId>soap-client</artifactId>
    <version>1.0.0</version>
    <name>soap-client</name>
    <description>Spring Boot SOAP Client with Jakarta</description>
    
    <properties>
        <java.version>17</java.version>
        <jakarta.xml.ws-api.version>4.0.0</jakarta.xml.ws-api.version>
        <jakarta.jws-api.version>3.0.0</jakarta.jws-api.version>
    </properties>
    
    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>
        
        <!-- Jakarta XML Web Services API -->
        <dependency>
            <groupId>jakarta.xml.ws</groupId>
            <artifactId>jakarta.xml.ws-api</artifactId>
            <version>${jakarta.xml.ws-api.version}</version>
        </dependency>
        
        <!-- Jakarta Web Services API -->
        <dependency>
            <groupId>jakarta.jws</groupId>
            <artifactId>jakarta.jws-api</artifactId>
            <version>${jakarta.jws-api.version}</version>
        </dependency>
        
        <!-- Implementación de Jakarta XML Web Services -->
        <dependency>
            <groupId>com.sun.xml.ws</groupId>
            <artifactId>jaxws-rt</artifactId>
            <version>4.0.0</version>
        </dependency>
        
        <!-- Jakarta Annotations API -->
        <dependency>
            <groupId>jakarta.annotation</groupId>
            <artifactId>jakarta.annotation-api</artifactId>
            <version>2.1.1</version>
        </dependency>
        
        <!-- JAXB Runtime for XML Processing -->
        <dependency>
            <groupId>org.glassfish.jaxb</groupId>
            <artifactId>jaxb-runtime</artifactId>
        </dependency>
        
        <!-- Spring WS Core -->
        <dependency>
            <groupId>org.springframework.ws</groupId>
            <artifactId>spring-ws-core</artifactId>
        </dependency>
        
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
        </dependency>
    </dependencies>
    
    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>
            
            <!-- CXF Maven Plugin para generar clases Java desde WSDL -->
            <plugin>
                <groupId>org.apache.cxf</groupId>
                <artifactId>cxf-codegen-plugin</artifactId>
                <version>4.0.3</version>
                <executions>
                    <execution>
                        <id>generate-sources</id>
                        <phase>generate-sources</phase>
                        <configuration>
                            <sourceRoot>${project.build.directory}/generated-sources/cxf</sourceRoot>
                            <wsdlOptions>
                                <wsdlOption>
                                    <wsdl><!-- URL de tu WSDL aquí --></wsdl>
                                    <packagenames>
                                        <packagename>com.example.soap.client.generated</packagename>
                                    </packagenames>
                                </wsdlOption>
                            </wsdlOptions>
                        </configuration>
                        <goals>
                            <goal>wsdl2java</goal>
                        </goals>
                    </execution>
                </executions>
            </plugin>
        </plugins>
    </build>
</project>

