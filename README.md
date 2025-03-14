
﻿<!DOCTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Smart File Converter AI</title>
    <link rel="stylesheet" href="styles.css">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/pdf.js/2.14.305/pdf.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jszip/3.10.1/jszip.min.js"></script>
    <script src="script.js"></script>
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }
        body {
            font-family: Arial, sans-serif;
            background-color: #eef1f7;
            color: #333;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
        }
        header {
            background: linear-gradient(90deg, #007bff, #00c6ff);
            color: white;
            padding: 20px;
            font-size: 24px;
            width: 100%;
            text-align: center;
            box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.1);
        }
        .ad-space {
            width: 100%;
            height: 90px;
            background: #ddd;
            text-align: center;
            line-height: 90px;
            margin: 10px 0;
        }
        .container {
            display: flex;
            flex-direction: row;
            width: 90%;
            max-width: 1200px;
            margin: 20px auto;
        }
        .sidebar {
            width: 20%;
            background: #f8f9fa;
            padding: 20px;
            box-shadow: 2px 0px 5px rgba(0, 0, 0, 0.1);
        }
        .main-content {
            width: 60%;
            text-align: center;
            padding: 20px;
            background: white;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            border-radius: 10px;
        }
        .upload-section {
            margin: 20px 0;
        }
        .footer {
            width: 100%;
            background: #333;
            color: white;
            text-align: center;
            padding: 10px;
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <div class="ad-space">Ad Space (Top)</div>
    <header>
        <h1>Smart File Converter AI</h1>
        <p>PDF, JPG, HTML और अन्य फाइल फॉर्मेट को बदलने का स्मार्ट तरीका!</p>
    </header>
    <div class="container">
        <aside class="sidebar">
            <h3>Login / Register</h3>
            <button>Login</button>
            <button>Register</button>
            <h3>Advertisements</h3>
            <div style="height: 200px; background: #ddd; margin: 10px 0;">Ad Space</div>
            <div style="height: 200px; background: #ddd;">Ad Space</div>
        </aside>
        <main class="main-content">
            <div class="upload-section">
                <input type="file" id="fileInput" multiple>
                <select id="conversionType">
                    <option value="pdf-to-jpg">PDF to JPG</option>
                    <option value="jpg-to-pdf">JPG to PDF</option>
                    <option value="html-to-pdf">HTML to PDF</option>
                    <option value="pdf-to-word">PDF to WORD</option>
                    <option value="pdf-to-excel">PDF to EXCEL</option>
                    <option value="pdf-to-powerpoint">PDF to POWERPOINT</option>
                    <option value="merge-pdf">Merge PDF</option>
                    <option value="split-pdf">Split PDF</option>
                    <option value="compress-pdf">Compress PDF</option>
                </select>
                <button onclick="convertFile()">Convert करें</button>
            </div>
            <section id="outputSection" class="hidden">
                <h2>Converted Files</h2>
                <a id="downloadLink" href="#" download="converted-file">डाउनलोड करें</a>
            </section>
        </main>
        <aside class="sidebar">
            <h3>More Tools</h3>
            <button>OCR PDF</button>
            <button>Rotate PDF</button>
            <button>Edit PDF</button>
            <button>Add Page Numbers</button>
            <button>Add Watermark</button>
        </aside>
    </div>
    <footer class="footer">
        <p>&copy; 2025 Smart File Converter AI. All rights reserved.</p>
    </footer>
    <div class="ad-space">Ad Space (Bottom)</div>
    <script>
        function convertFile() {
            const fileInput = document.getElementById('fileInput');
            const conversionType = document.getElementById('conversionType').value;
            const downloadLink = document.getElementById('downloadLink');
            const outputSection = document.getElementById('outputSection');
            
            if (fileInput.files.length === 0) {
                alert('कृपया एक फाइल चुनें!');
                return;
            }

            const file = fileInput.files[0];
            const reader = new FileReader();
            reader.onload = function(event) {
                const blob = new Blob([event.target.result], { type: "application/octet-stream" });
                const url = URL.createObjectURL(blob);
                
                let newFileName = "converted-file";
                if (conversionType === "pdf-to-jpg") {
                    newFileName += ".jpg";
                } else if (conversionType === "jpg-to-pdf") {
                    newFileName += ".pdf";
                }
                
                downloadLink.href = url;
                downloadLink.download = newFileName;
                outputSection.classList.remove("hidden");
            };
            reader.readAsArrayBuffer(file);
        }
    </script>
</body>
</html>
