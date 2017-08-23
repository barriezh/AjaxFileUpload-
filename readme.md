### ajaxFileUpload

``` html


<body>
 	<script src="jquery-1.7.1.js" type="text/javascript"></script>
    <script src="ajaxfileupload.js" type="text/javascript"></script>
    <p><input type="file" id="file1" name="file" /></p>
    <input type="button" value="上传" />
    <p><img id="img1" alt="上传成功啦" src="" /></p>
</body>
<script src="jquery-1.7.1.js" type="text/javascript"></script>
    <script src="ajaxfileupload.js" type="text/javascript"></script>
    <script type="text/javascript">
        $(function () {
            $(":button").click(function () {
                ajaxFileUpload();
            })
        })
        function ajaxFileUpload() {
            $.ajaxFileUpload
            (
                {
                    url: 'upload.php', //用于文件上传的服务器端请求地址
                    secureuri: false, //是否需要安全协议，一般设置为false
                    fileElementId: 'file1', //文件上传域的ID
                    dataType: 'json', //返回值类型 一般设置为json
                    data: {"key":"value"},
                    success: function (data, status)  //服务器成功响应处理函数
                    {
                        $("#img1").attr("src", data.imgurl);
                        if (typeof (data.error) != 'undefined') {
                            if (data.error != '') {
                                alert(data.error);
                            } else {
                                alert(data.msg);
                            }
                        }
                    },
                    error: function (data, status, e)//服务器响应失败处理函数
                    {
                        alert(e);
                    }
                }
            )
            return false;
        }
    </script>


```