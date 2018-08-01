
import java.awt.image.BufferedImage;
import java.io.File;
import java.io.IOException;


import javax.imageio.*;


public class ImageData {
	public BufferedImage img;
	private BufferedImage original;
	
	private int trimLeft;
	private int trimTop;
	private int trimRight;
	private int trimBottom;
	
	//create imagedata object from path. Image DataObjects have simple methods
	//for cropping transposing and getting floating point values of colors.
	ImageData(String path){
		try{
			original = ImageIO.read(new File(path));
			img = ImageIO.read(new File(path));
		}catch(IOException e){
			e.printStackTrace();
		}
		trimLeft =0;
		trimRight =0;
		trimTop = 0;
		trimBottom = 0;
	}
	
	int getWidth(){
		return img.getWidth();
	}
	
	int getHeight(){
		return img.getHeight();
	}
	
	//Returns Pixel object of a picture element RGB value
	//returns null if invalid indices are given, arrayindexoutofbounds caught and
	//printed to sys.err for debugging purposes.
	Pixel getPixel(int x, int y){
		int pixel;
		try {
			pixel = img.getRGB(x, y);
			return new Pixel(pixel);
		} catch (ArrayIndexOutOfBoundsException e) {
			e.printStackTrace();
			System.out.println();
			System.err.println("\nTried to set a pixel not in the image at Row = " + y + " Col = " + x + "\n\n");
		}

		return null;
		
	}
	
	
	//returns pixel object with members red, green, blue as floating point values
	//deprecated
	Pixel getRGB(int pixel){
		if(pixel <=-1)
			return new Pixel(pixel);
		
		return null;
	}
	//returns floating point value of Red value, if out of bounds returns 2.0f
	float getRed(int x, int y){
		if(y<img.getHeight()&& x<img.getWidth()&&y >0 &&x > 0)
			return getPixel(x,y).getRed();
		return 2.0f;
	}
	//returns floating point value of green value, if out of bounds returns 2.0f
	float getGreen(int x, int y){
		if(y<img.getHeight()&& x<img.getWidth()&&y >0 &&x > 0)
			return getPixel(x,y).getGreen();
		return 2.0f;
	}
	//returns floating point value of blue value, if out of bounds returns 2.0f
	float getBlue(int x, int y){
		if(y<img.getHeight()&& x<img.getWidth()&&y >0 &&x > 0)
			return getPixel(x,y).getBlue();
		return 2.0f;
	}
	
	//Set pixel in image to color of another pixel 
	//if invalid indices are given error is printed to sys.err (for debugging purposes
	void setPixel(int col, int row, Pixel p){
		try{
			img.setRGB(col, row, p.getIntValue() );
		}catch(ArrayIndexOutOfBoundsException e){
			e.printStackTrace();
			System.out.println();
			System.err.println("\nTried to set a pixel not in the image at Row = " + row + " Col = " + col + "\n\n");
		}
	}
	
	//Set pixel in image to color of integer value color 
	//if invalid indices are given error is printed to sys.err (for debugging purposes)
	//You can either generate a color using Pixel.getIntColor(float, float float);
	//for instance use Pixel.getIntColor(0.0f,0.0f,0.0f) for black
	//or I pre-coded three colors Pixel.RED, Pixel.Green and Pixel.Blue
	//or the third way is use ImageData.getRGB(int h, int w)
	void setPixel(int col, int row, int color){
		try{
			img.setRGB(col, row , color);
		}catch(ArrayIndexOutOfBoundsException e){
			e.printStackTrace();
			System.out.println();
			System.err.println("\nTried to set a pixel not in the image at Row = " + row + " Col = " + col + "\n\n");
		}
		
	}
	
	//transposes the image rotating it 90 degrees, running this twice returns the original image.
	void TransPose(){
		BufferedImage temp = new BufferedImage(img.getHeight(), img.getWidth(),BufferedImage.TYPE_INT_ARGB);
		for(int i = 0; i<img.getWidth(); i++)
			for( int j =0; j< img.getHeight(); j++){
				temp.setRGB(j, i, img.getRGB(i, j));
			}
		img = temp;
	}
	
	//remove one column from the left hand side of the picture plus any other rows designated for trimming
	void trimLeft(){
		this.trimLeft += 1;
		trim();
	}
	
	//remove one row from the top side of the picture plus any rows designated for trimming
	void trimTop(){
		this.trimTop +=1;
		trim();
	}
	//remove one column from the right hand side of the picture plus any other rows designated for trimming
	void trimRight(){
		this.trimRight +=1;
		trim();
	}
	//remove one row from the bottom side of the picture plus any rows designated for trimming
	void trimBottom(){
		this.trimBottom += 1;
		trim();
	}
	
	//before running trim you can set how many rows to remove when you next call it.
	//if there is already trim values set these will add to it
	void setTopTrim(int y){
		this.trimTop += y;
	}
	//before running trim you can set how many columns to remove when you next call it.
		//if there is already trim values set these will add to it
	void setLeftTrim(int x){
		this.trimLeft += x;
	}
	
	//before running trim you can set how many rows to remove when you next call it.
		//if there is already trim values set these will add to it
		void setBottomTrim(int y){
			this.trimBottom += y;
		}
		//before running trim you can set how many columns to remove when you next call it.
			//if there is already trim values set these will add to it
		void setRightTrim(int x){
			this.trimRight += x;
		}
	
	//crops the image based on the trim values set
	void trim(){
		this.img = img.getSubimage(trimLeft,trimTop, img.getWidth()- trimLeft - trimRight, img.getHeight() - trimTop - trimBottom);
		this.trimLeft =0;
		this.trimRight =0;
		this.trimTop = 0;
		this.trimBottom = 0;
	}
	
	//returns original unedited image
	public BufferedImage getOriginal(){
		return original;
	}
	
	

	
	
}
