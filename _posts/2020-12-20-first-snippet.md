---
category: Main Category
url_path: ''
title: 'Brief title here'
type: 'JAVA'

layout: null
---

```java
package com.jmrchelani;// Java code to generate QR code

import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.io.File;
import java.io.IOException;
import java.util.HashMap;
import java.util.Map;
import com.google.zxing.BarcodeFormat;
import com.google.zxing.EncodeHintType;
import com.google.zxing.MultiFormatWriter;
import com.google.zxing.NotFoundException;
import com.google.zxing.WriterException;
import com.google.zxing.client.j2se.MatrixToImageWriter;
import com.google.zxing.common.BitMatrix;
import com.google.zxing.qrcode.decoder.ErrorCorrectionLevel;

import javax.swing.*;

class Main implements ActionListener {

    // Function to create the QR code
    public static void createQR(String data, String path,
                                String charset, Map hashMap,
                                int height, int width)
            throws WriterException, IOException
    {

        BitMatrix matrix = new MultiFormatWriter().encode(
                new String(data.getBytes(charset), charset),
                BarcodeFormat.QR_CODE, width, height);

        MatrixToImageWriter.writeToFile(
                matrix,
                path.substring(path.lastIndexOf('.') + 1),
                new File(path));
    }
    static JFrame frame;
    // Driver code
    public static void main(String[] args)
            throws WriterException, IOException,
            NotFoundException
    {

        // The data that the QR code will contain
        String data = "jmrchelani.github.io";

        // The path where the image will get saved
        String path = "demo.png";

        // Encoding charset
        String charset = "UTF-8";

        Map<EncodeHintType, ErrorCorrectionLevel> hashMap
                = new HashMap<EncodeHintType,
                ErrorCorrectionLevel>();

        hashMap.put(EncodeHintType.ERROR_CORRECTION,
                ErrorCorrectionLevel.L);

        // Create the QR code and save
        // in the specified folder
        // as a jpg file
        createQR(data, path, charset, hashMap, 200, 200);
        System.out.println("QR Code Generated!!! ");

        frame=new JFrame("Image on Click");
        frame.setSize(500,500);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.getContentPane().setBackground(Color.white);
        frame.setLayout(new FlowLayout());
        //Create a button
        JButton button=new JButton("Display");
        frame.add(button);
        //Create an object

        //Associate ActionListener with button
        Main a = new Main();
        button.addActionListener(a);
        //Display the frame
        frame.setVisible(true);
    }
    public void actionPerformed(ActionEvent e)
    {
        //Display Image
        ImageIcon icon=new ImageIcon("demo.png");
        JLabel label=new JLabel(icon);
        frame.add(label);
        frame.pack();
        frame.setSize(500,500);
    }
}
```
