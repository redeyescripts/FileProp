# FileProp

## Monday project

```
using System;
using System.IO;

namespace Monday
{
    class Program
    {
        static void Main(string[] args)
        {
            string rootPath = @"C:\Users\opilane\samples";
            GetDirectories(rootPath);
            GetFiles(rootPath);
        }
        public static void GetDirectories(string path)
        {
            string[] allDirectories = Directory.GetDirectories(path, " * ", SearchOption.AllDirectories);
            string filePath = @"C:\Users\opilane\Monday\directoriesData.txt";

            File.WriteAllLines(filePath, allDirectories);  
        }
        public static void GetFiles(string path)
        {
            string[] allfiles = Directory.GetFiles(path, "*.*", SearchOption.AllDirectories);
            string filePath = @"C:\Users\opilane\Monday\filesData.txt";
            File.WriteAllLines(filePath, allfiles);
        }
        
    }
}


```

## FileProps

```
using System;
using System.Collections.Generic;
using System.IO;

namespace FileProp
{
    class Program
    {
        static void Main(string[] args)
        {
            // get file names
            string rootPath = @"C:\Users\opilane\samples";
            string[] files = Directory.GetFiles(rootPath,"*.*",SearchOption.AllDirectories);
            List<string> lines = new List<string>();
            foreach (string file in files)
            {
                Console.WriteLine(file);


                // get file objects

                var fileData = new FileInfo(file);
                string filename = fileData.Name;
                string fileDirectory = fileData.DirectoryName;
                long filesSize = fileData.Length;
                Console.WriteLine($"File Name: {filename}; location: {fileDirectory}; Size {filesSize}");
                string line = $"File Name: {filename}; location: {fileDirectory}; Size {filesSize}byte";
                lines.Add(line);

            }

            string fileDataPath = @"C:\Users\opilane\samples\FileData.txt";

            File.WriteAllLines(fileDataPath, lines);




        }
    }
}

```

