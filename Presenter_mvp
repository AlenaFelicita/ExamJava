package Core.MVP;

import Configs.Config;
import Core.Models.Toy;

import java.util.ArrayList;
import java.util.List;
import java.util.PriorityQueue;

public class Presenter {
    private final Model model;
    private final IView view;

    public Presenter(IView view, String pathDb) {
        this.view = view;
        model = new Model(pathDb);
    }

    public void loadFromFile() {
        model.load();
        view.loadMessage();
    }

    public void putForDrawing() {
        if (model.currentDrawingService().putForDrawing(
                new Toy(view.getToyId(), view.getToyNaming(), view.getToyWeight())))
            view.savedItem();
        else
            view.saveError();
    }

    public void deleteFromDrawing() {
        if (model.currentDrawingService.getToys().size() == 0)
            view.emptyListMessage();
        else
            model.currentDrawingService().remove(view.getToyId());
    }

    public void saveToFile() {
        model.save();
        view.savedAll();
    }

    public void showAll() {
        if (model.currentDrawingService.getToys().size() == 0)
            view.emptyListMessage();
        else
            view.showAll(model.currentDrawingService.getToys());
    }

    public void clearAll() {
        if (model.currentDrawingService.getToys().size() == 0)
            view.emptyListMessage();
        else {
            if (view.clearAllDecision()) {
                model.currentDrawingService.getToys().clear();
                System.out.println("Все записи очищены!");
            }
        }
    }


    public void getDrawing() {
        PriorityQueue<Toy> priorityQueue = new PriorityQueue<>();
        Toy drawnToy;
        List<Toy> drawnToys = new ArrayList<>();
        if (model.currentDrawingService.getToys().size() != 0) {
            int times = view.getDrawTimes();
            priorityQueue.addAll(model.currentDrawingService().getToys());
            while (priorityQueue.size() < times) {
                priorityQueue.addAll(model.currentDrawingService().getToys());
            }
            for (int i = 0; i < times; i++) {
                drawnToy = priorityQueue.remove();
                view.showGetToy(drawnToy);
                drawnToys.add(drawnToy);
            }
            model.saveResult(Config.pathResult, drawnToys);
        } else
            view.emptyListMessage();


    }
}
