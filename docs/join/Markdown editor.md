<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="Content-Security-Policy" content="upgrade-insecure-requests">
    <title>Flying-book</title>
    
    <!-- 导入 SimpleMDE 的 CSS 文件 -->
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/simplemde/latest/simplemde.min.css">

    <!-- 导入 SimpleMDE 的 JavaScript 文件 -->
    <script src="https://cdn.jsdelivr.net/simplemde/latest/simplemde.min.js"></script>

    <style>
        /* Add styles for the title */
        body {
            font-family: Arial, sans-serif;
        }

        h1 {
            text-align: center;
            color: #333; /* Adjust the color as needed */
        }

        /* Add styles for the button container */
        .button-container {
            text-align: right;
            margin-right: 20px; /* Adjust the margin as needed */
        }

        /* Add styles for the button */
        #saveButton {
            font-family: '华文宋体', 'STSong', 'SimSun', sans-serif; /* Change the font-family */
            font-size: 16px; /* Adjust the font size */
            background-color: #4CAF50; /* Green background color */
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }

        #saveButton:hover {
            background-color: #45a049; /* Darker green on hover */
        }
    </style>

    <script>
        document.addEventListener('DOMContentLoaded', () => {
            var simplemde = new SimpleMDE({ element: document.getElementById("MyID") });

            document.getElementById("saveButton").addEventListener("click", function() {
                // 获取 SimpleMDE 编辑器中的内容
                var markdownContent = simplemde.value();
                var xhr = new XMLHttpRequest();
                xhr.open("POST", "http://g34hsn.natappfree.cc/receiver/GetMdServlet", true);
                xhr.setRequestHeader("Content-Type", "text/plain");
                xhr.onload = function() {
                    if (xhr.status === 200) {
                        // 上传成功，可以在这里处理后端返回的响应
                        console.log("Response received:", xhr.responseText);
                        alert("操作成功！");
                    } else {
                        // 上传失败
                        console.error("File upload failed");
                    }
                };
                xhr.send(markdownContent);
            });
        });
    </script>
</head>
<body>
    <!-- Add a title for the page -->
    <h1>FZU飞跃手册 Markdown编辑器</h1>

    <div>
        <textarea id="MyID" rows="10" cols="50"></textarea>
    </div>
    <!-- Move the button to the right -->
    <div class="button-container">
        <button id="saveButton">保存并上传</button>
    </div>
</body>
</html>
