# hello-world
package com.kgc.demoeveryday;

import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.FileReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.OutputStreamWriter;
import java.io.Reader;
import java.io.UnsupportedEncodingException;

//将文件test.txt 写入到新文件test1.txt当中去。

public class ReaderAndWriter {
	public static void main(String[] args) {
//		建立一个文件字节输入流fis
		FileInputStream fis = null;
//		建立一个输入字符流ir
		InputStreamReader ir = null;
//		建立一个字符输入缓冲流br
		BufferedReader br = null;
//		建立一个文件输出字节流fos
		FileOutputStream fos = null;
//		建立一个输出字符输出流osw
		OutputStreamWriter osw = null;
//		建立一个字符输出缓冲流bw
		BufferedWriter bw = null;
//		建立一个输入字符流rd，父类引用rd指向子类对象Bufferedreader
		Reader rd=null;
//		建立一个输入字符缓冲流newbr
		BufferedReader newbr=null;
		try {
//			读取文件test.txt到对象fis
			fis = new FileInputStream("D:\\javakaifa\\test.txt");
//			将fis采用gb2312形式包装成一个输入字符流ir
			ir = new InputStreamReader(fis, "gb2312");
//			将ir包装成字符输入缓冲流
			br = new BufferedReader(ir);
//			将文件test.txt写到字节输入流fos中
			fos = new FileOutputStream("D:\\javakaifa\\test2.txt");
//			将字节输出流对象包装成字符输出流osw对象中
			osw = new OutputStreamWriter(fos);
//			将输出对象包装成缓冲字符输出流osw，利用bufferedwriter的特有属性来
			bw = new BufferedWriter(osw);
//			定义一个新的字符串变量words
			String words = null;
//			读取br中的所有字符串输出到words中，直到末尾
			while ((words=br.readLine()) != null) {
//				循环输出words内容
				System.out.println("内容是:"+words);
//				将字符串words当中的所有内容追加到bw对象中，最后写入文件test.txt
				bw.append(words);
				
			}
			bw.append("我爱你家国万里，无忧无虑");
//			强制清空缓存，防止bw出现任务未完成的情况
			bw.flush();
			System.out.println("***********************************");
			rd=new FileReader("D:\\javakaifa\\test2.txt");
			newbr=new BufferedReader(rd);
			String lines=null;
//			输出newbr读取到的test2的信息
			while((lines=newbr.readLine())!=null){
				
				System.out.println(lines);
			}
			

		} catch (FileNotFoundException e) {
			e.printStackTrace();
		} catch (UnsupportedEncodingException e) {
			e.printStackTrace();
		} catch (IOException e) {
			e.printStackTrace();
		} finally {

			try {
//				关闭输入输出流释放内存资源
				bw.close();
				osw.close();
				fos.close();
				br.close();
				ir.close();
				fis.close();
				newbr.close();
				rd.close();
				
			} catch (IOException e) {
				e.printStackTrace();
			}

		}

	}
}

/*
输入输出控制是一个比较重要的操作，他可以将字符写入文件，也可以将对象写入文件，这是非常重要的，还有视频流的输入和输出。
输入流：
inputstream 
reader  bufferedReader fileReader fileinputReader
datainputstream


输出流
outputstream  字符输出流

writer     字节输出流

dataoutputstream  二进制文件输出流
*/




