import java.io.File;
import java.io.IOException;
import java.util.HashMap;
import java.util.Map;
import javax.xml.parsers.DocumentBuilder;
import javax.xml.parsers.DocumentBuilderFactory;
import javax.xml.parsers.ParserConfigurationException;
import org.w3c.dom.Document;
import org.w3c.dom.Element;
import org.w3c.dom.NodeList;
import org.xml.sax.SAXException;

public class EJBAnalyzer {
    public static void main(String[] args) {
        try {
            // Parse the EJB deployment descriptor
            Document ejbDocument = parseEjbDeploymentDescriptor("path/to/ejb-jar.xml");

            // Analyze EJB types
            Map<String, Integer> ejbTypes = analyzeEjbTypes(ejbDocument);
            System.out.println("EJB Types:");
            ejbTypes.forEach((type, count) -> System.out.println(type + ": " + count));

            // Analyze EJB interfaces
            Map<String, Integer> ejbInterfaces = analyzeEjbInterfaces(ejbDocument);
            System.out.println("EJB Interfaces:");
            ejbInterfaces.forEach((type, count) -> System.out.println(type + ": " + count));

            // Analyze EJB transactional attributes
            Map<String, Integer> ejbTransactional = analyzeEjbTransactional(ejbDocument);
            System.out.println("EJB Transactional Attributes:");
            ejbTransactional.forEach((type, count) -> System.out.println(type + ": " + count));

            // Analyze Java version from manifest
            String javaVersion = analyzeJavaVersion("path/to/application.war");
            System.out.println("Java Version: " + javaVersion);
        } catch (ParserConfigurationException | SAXException | IOException e) {
            e.printStackTrace();
        }
    }

    // Implement the following methods:
    private static Document parseEjbDeploymentDescriptor(String path) { /* ... */ }
    private static Map<String, Integer> analyzeEjbTypes(Document doc) { /* ... */ }
    private static Map<String, Integer> analyzeEjbInterfaces(Document doc) { /* ... */ }
    private static Map<String, Integer> analyzeEjbTransactional(Document doc) { /* ... */ }
    private static String analyzeJavaVersion(String path) { /* ... */ }
}





--------import java.io.File;
import java.io.FileInputStream;
import java.io.IOException;
import java.util.HashMap;
import java.util.Map;
import javax.xml.parsers.DocumentBuilder;
import javax.xml.parsers.DocumentBuilderFactory;
import javax.xml.parsers.ParserConfigurationException;
import org.w3c.dom.Document;
import org.w3c.dom.Element;
import org.w3c.dom.NodeList;
import org.xml.sax.SAXException;

public class EJBAnalyzer {

    public static void main(String[] args) {
        String ejbDescriptorPath = "path/to/ejb-jar.xml";
        String warFilePath = "path/to/application.war";

        try {
            Document ejbDocument = parseEjbDeploymentDescriptor(ejbDescriptorPath);

            // Análisis de tipos de EJB
            Map<String, Integer> ejbTypes = analyzeEjbTypes(ejbDocument);
            System.out.println("EJB Types:");
            ejbTypes.forEach((type, count) -> System.out.println(type + ": " + count));

            // Análisis de interfaces de EJB
            Map<String, Integer> ejbInterfaces = analyzeEjbInterfaces(ejbDocument);
            System.out.println("EJB Interfaces:");
            ejbInterfaces.forEach((type, count) -> System.out.println(type + ": " + count));

            // Análisis de atributos transaccionales de EJB
            Map<String, Integer> ejbTransactional = analyzeEjbTransactional(ejbDocument);
            System.out.println("EJB Transactional Attributes:");
            ejbTransactional.forEach((type, count) -> System.out.println(type + ": " + count));

            // Análisis de la versión de Java
            String javaVersion = analyzeJavaVersion(warFilePath);
            System.out.println("Java Version: " + javaVersion);
        } catch (Exception e) {
            System.err.println("Error: " + e.getMessage());
            e.printStackTrace();
        }
    }

    private static Document parseEjbDeploymentDescriptor(String path) throws ParserConfigurationException, SAXException, IOException {
        File file = new File(path);
        if (!file.exists() || !file.isFile()) {
            throw new IOException("EJB deployment descriptor file not found: " + path);
        }

        DocumentBuilderFactory factory = DocumentBuilderFactory.newInstance();
        DocumentBuilder builder = factory.newDocumentBuilder();
        try (FileInputStream fis = new FileInputStream(file)) {
            return builder.parse(fis);
        }
    }

    private static Map<String, Integer> analyzeEjbTypes(Document doc) {
        Map<String, Integer> ejbTypes = new HashMap<>();
        NodeList beans = doc.getElementsByTagName("session"); // Ejemplo para session beans

        for (int i = 0; i < beans.getLength(); i++) {
            Element bean = (Element) beans.item(i);
            String type = bean.getAttribute("ejb-class");  // Cambia el campo según el XML
            ejbTypes.put(type, ejbTypes.getOrDefault(type, 0) + 1);
        }
        return ejbTypes;
    }

    private static Map<String, Integer> analyzeEjbInterfaces(Document doc) {
        Map<String, Integer> ejbInterfaces = new HashMap<>();
        NodeList interfaces = doc.getElementsByTagName("remote"); // O el nodo adecuado

        for (int i = 0; i < interfaces.getLength(); i++) {
            Element interfaceElement = (Element) interfaces.item(i);
            String interfaceType = interfaceElement.getTextContent().trim();
            ejbInterfaces.put(interfaceType, ejbInterfaces.getOrDefault(interfaceType, 0) + 1);
        }
        return ejbInterfaces;
    }

    private static Map<String, Integer> analyzeEjbTransactional(Document doc) {
        Map<String, Integer> ejbTransactional = new HashMap<>();
        NodeList transactions = doc.getElementsByTagName("transaction-type"); // O el nodo adecuado

        for (int i = 0; i < transactions.getLength(); i++) {
            Element transactionElement = (Element) transactions.item(i);
            String transactionType = transactionElement.getTextContent().trim();
            ejbTransactional.put(transactionType, ejbTransactional.getOrDefault(transactionType, 0) + 1);
        }
        return ejbTransactional;
    }

    private static String analyzeJavaVersion(String warPath) throws IOException {
        File file = new File(warPath);
        if (!file.exists() || !file.isFile()) {
            throw new IOException("WAR file not found: " + warPath);
        }

        // Ejemplo: Extraer versión de un archivo MANIFEST dentro del WAR
        try (FileInputStream fis = new FileInputStream(file)) {
            // Aquí iría la lógica para leer la versión de Java en MANIFEST
            // Para simplificar, devolvemos un valor simulado
            return "Java 1.8";
        }
    }
}



