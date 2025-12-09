### Pour creer un projet java fx avec maven 
    mvn archetype:generate -DgroupId=com.example -DartifactId=myproject -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false

### modifier le pom.xml en ceci : 
    <project xmlns="http://maven.apache.org/POM/4.0.0"
            xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
            xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
        <modelVersion>4.0.0</modelVersion>

        <groupId>com.example</groupId>
        <artifactId>demo-javafx</artifactId>
        <version>1.0-SNAPSHOT</version>

        <properties>
            <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
            <maven.compiler.source>17</maven.compiler.source>
            <maven.compiler.target>17</maven.compiler.target>
            <javafx.version>21.0.1</javafx.version>
        </properties>

        <dependencies>
            <!-- Dépendances JavaFX -->
            <dependency>
                <groupId>org.openjfx</groupId>
                <artifactId>javafx-controls</artifactId>
                <version>${javafx.version}</version>
            </dependency>
            <dependency>
                <groupId>org.openjfx</groupId>
                <artifactId>javafx-fxml</artifactId>
                <version>${javafx.version}</version>
            </dependency>
        </dependencies>

        <!-- Plugin pour exécuter JavaFX -->
        <build>
            <plugins>
                <plugin>
                    <groupId>org.openjfx</groupId>
                    <artifactId>javafx-maven-plugin</artifactId>
                    <version>0.0.8</version>
                    <configuration>
                        <mainClass>com.example.App</mainClass>
                    </configuration>
                </plugin>
            </plugins>
        </build>
    </project>

### modifier dans le **src/main/java/com/example/App.java** en ceci : 
    package com.example;

    import javafx.application.Application;
    import javafx.scene.Scene;
    import javafx.scene.control.Label;
    import javafx.stage.Stage;

    public class App extends Application {

        @Override
        public void start(Stage stage) {
            Label label = new Label("Hello JavaFX + Maven !");
            Scene scene = new Scene(label, 400, 200);

            stage.setTitle("JavaFX Maven");
            stage.setScene(scene);
            stage.show();
        }

        public static void main(String[] args) {
            launch();
        }
    }

### executer le projet : 
    mvn javafx:run
### ou
    mvn clean javafx:run