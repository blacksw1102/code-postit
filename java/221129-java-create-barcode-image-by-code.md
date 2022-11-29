```java
import java.awt.image.BufferedImage;

import org.krysalis.barcode4j.HumanReadablePlacement;
import org.krysalis.barcode4j.impl.code128.Code128Bean;
import org.krysalis.barcode4j.output.bitmap.BitmapCanvasProvider;
import org.krysalis.barcode4j.tools.UnitConv;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

public class BarcodeUtil {

    static private final int DPI = 100;
    static private final float WIDTH = 5.0f;
    static private final double HEIGHT = 65;
	
    static public synchronized BufferedImage getBufferedBarcodeImage(String code) {

        BufferedImage barcodeImage = null;
        
    	if(code == null) {
    		return null;
        }
    	
        try {
        	Code128Bean bean = new Code128Bean();
            bean.setMsgPosition(HumanReadablePlacement.HRP_NONE); // 이미지 하단에 코드 값 미노출
        	bean.setModuleWidth(UnitConv.in2mm(WIDTH / DPI));
        	bean.setHeight(HEIGHT);

            BitmapCanvasProvider canvas = new BitmapCanvasProvider(
                	DPI, BufferedImage.TYPE_BYTE_BINARY, false, 0);

            bean.generateBarcode(canvas, code);
            barcodeImage = canvas.getBufferedImage();
            canvas.finish();
        }
        catch(Exception e) {
			// exception
        }
        
        return barcodeImage;
    }

}

```