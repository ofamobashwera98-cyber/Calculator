# JavaFX Calculator Design

## Objective
To create a simple calculator application using JavaFX that can perform basic arithmetic operations such as addition, subtraction, multiplication, and division.

---

## Features
- Number buttons (0–9)
- Arithmetic operators (+, -, *, /)
- Clear button (C)
- Equal button (=)
- Stylish light purple background
- Non-editable display field

---

## Technologies Used
- Java
- JavaFX
- NetBeans IDE

---

## Source Code

```java
package calculatordesign;

import javafx.application.Application;
import static javafx.application.Application.launch;
import javafx.geometry.Pos;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.control.TextField;
import javafx.scene.layout.GridPane;
import javafx.scene.layout.VBox;
import javafx.stage.Stage;

public class CalculatorDesign extends Application {

    double firstnumber = 0;
    String operator ="";

    @Override
    public void start(Stage primaryStage) {

        TextField display= new TextField();
        display.setEditable(false);
        display.setAlignment(Pos.CENTER_RIGHT);
        display.setPrefHeight(60);
        display.setStyle("-fx-font-size: 24px;");

        GridPane grid= new GridPane();
        grid.setStyle("-fx-background-color: #D8BFD8;");
        grid.setHgap(10);
        grid.setVgap(10);

        Button B1 = new Button("7");
        Button B2 = new Button("8");
        Button B3 = new Button("9");
        Button B4 = new Button("*");

        Button B5 = new Button("4");
        Button B6 = new Button("5");
        Button B7 = new Button("6");
        Button B8 = new Button("/");

        Button B9 = new Button("1");
        Button B10 = new Button("2");
        Button B11 = new Button("3");
        Button B12 = new Button("-");

        Button B13 = new Button("C");
        Button B14 = new Button("0");
        Button B15 = new Button("=");
        Button B16 = new Button("+");

        Button[] buttons = {
            B1,B2,B3,B4,B5,B6,B7,B8,
            B9,B10,B11,B12,B13,B14,B15,B16
        };

        for(Button b : buttons){
            b.setPrefSize(70,70);
        }

        grid.add(B1, 0, 0);
        grid.add(B2, 1, 0);
        grid.add(B3, 2, 0);
        grid.add(B4, 3, 0);

        grid.add(B5, 0, 1);
        grid.add(B6, 1, 1);
        grid.add(B7, 2, 1);
        grid.add(B8, 3, 1);

        grid.add(B9, 0, 2);
        grid.add(B10, 1, 2);
        grid.add(B11, 2, 2);
        grid.add(B12, 3, 2);

        grid.add(B13, 0, 3);
        grid.add(B14, 1, 3);
        grid.add(B15, 2, 3);
        grid.add(B16, 3, 3);

        // Number buttons
        B1.setOnAction(e -> display.appendText("7"));
        B2.setOnAction(e -> display.appendText("8"));
        B3.setOnAction(e -> display.appendText("9"));

        B5.setOnAction(e -> display.appendText("4"));
        B6.setOnAction(e -> display.appendText("5"));
        B7.setOnAction(e -> display.appendText("6"));

        B9.setOnAction(e -> display.appendText("1"));
        B10.setOnAction(e -> display.appendText("2"));
        B11.setOnAction(e -> display.appendText("3"));

        B14.setOnAction(e -> display.appendText("0"));

        // Operators
        B4.setOnAction(e -> {
            firstnumber = Double.parseDouble(display.getText());
            operator = "*";
            display.clear();
        });

        B8.setOnAction(e -> {
            firstnumber = Double.parseDouble(display.getText());
            operator = "/";
            display.clear();
        });

        B12.setOnAction(e -> {
            firstnumber = Double.parseDouble(display.getText());
            operator = "-";
            display.clear();
        });

        B16.setOnAction(e -> {
            firstnumber = Double.parseDouble(display.getText());
            operator = "+";
            display.clear();
        });

        // Equal button
        B15.setOnAction(e -> {
            double secondnumber = Double.parseDouble(display.getText());
            double result = 0;

            switch(operator) {
                case "+":
                    result = firstnumber + secondnumber;
                    break;

                case "-":
                    result = firstnumber - secondnumber;
                    break;

                case "*":
                    result = firstnumber * secondnumber;
                    break;

                case "/":
                    result = firstnumber / secondnumber;
                    break;
            }

            display.setText(String.valueOf(result));
        });

        // Clear button
        B13.setOnAction(e -> {
            display.clear();
            firstnumber = 0;
            operator = "";
        });

        VBox root= new VBox(20, display, grid);

        Scene scene= new Scene(root, 320, 250);

        primaryStage.setTitle("Calculator");
        primaryStage.setScene(scene);
        primaryStage.setResizable(false);
        primaryStage.show();
    }

    public static void main(String[] args) {
        launch(args);
    }
}
