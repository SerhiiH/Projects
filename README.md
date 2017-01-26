import java.util.*;

class Rectangles {
	private class Rectangle {
		private int width;
		private int height;
		
		Rectangle(int w, int h) {
			width = w;
			height = h;		
		}
		
		public int getSquare() {
			return width * height;
		}
		public int getPerimeter() {
			return 2 * (width + height);
		}
	}
	private ArrayList<Rectangle> rectanglesList;
	
	private Rectangles() {
		rectanglesList = new ArrayList<Rectangle>();
	}
	
	public static Rectangles newInstance() {
		return new Rectangles();
	}
	public void addRectangle(int w, int h) {
		check(w, h);
		rectanglesList.add(new Rectangle(w, h));
	}
	private void check(int w, int h) {
		if (w < 0 || h < 0)
			throw new IllegalArgumentException();
	}
	public int getTotalSquareOfRectangles() {
		int sum = 0;
		
		for (Rectangle tmpRectangle : rectanglesList) {
			sum += tmpRectangle.getSquare();
		}
		return sum;
	}
}

public class RectangleRunner {
	public static void main(String[] args) {
		Rectangles rectangles = Rectangles.newInstance();
		rectangles.addRectangle(10, 20);
		rectangles.addRectangle(5, 10);
		rectangles.addRectangle(6, 4);
		System.out.println("Total square - " + rectangles.getTotalSquareOfRectangles());
	} 
}
