package UI;

import Configs.Config;
import Core.MVP.Presenter;
import Core.Models.Toy;

import java.util.Scanner;

@SuppressWarnings("ALL")
public class App {
    public static void buttonClick() {
        Presenter presenter = new Presenter(new ConsoleView(), Config.pathDb);
        presenter.loadFromFile();

        String command;

        while (true) {

            command = prompt("""

                     1 - Добавьте игрушку к рисунку
                     2 - Удалить игрушку из рисунка
                     3 - Сделайте рисунок (покажите результаты)
                     4 - Покажите игрушки для рисования
                     5 - Очистить все записи
                     6 - Сохраните все записи в файл
                     7 - Загрузите все записи из файла
                     8 - Выход
                    Сделайте свой выбор:\s""");
            if (command.equals("8")) {
                return;
            }
            try {
                switch (command) {
                    case "1" -> presenter.putForDrawing();
                    case "2" -> presenter.deleteFromDrawing();
                    case "3" ->
                            presenter.getDrawing();
                    case "4" -> presenter.showAll();
                    case "5" -> presenter.clearAll();
                    case "6" -> presenter.saveToFile();
                    case "7" -> presenter.loadFromFile();
                    default -> System.out.println("\n Команда не найдена!");
                }
            } catch (Exception e) {
                System.out.println("Error. " + e.getMessage());
            }
        }
    }

    private static String prompt(String message) {
        Scanner in = new Scanner(System.in);
        System.out.print(message);
        return in.nextLine();
    }

    private static Toy toyCreate() {
        int id = Integer.parseInt(prompt("Идентификатор игрушки: "));
        String name = prompt("Название игрушки: ");
        String weight = prompt("Вес игрушки: ");
        return (new Toy(id, name, Integer.parseInt(weight)));
    }
}
