<p>https://my.oschina.net/smartsmile/blog/814810</p>
<div class="cnblogs_Highlighter">
<pre class="brush:csharp;gutter:true;">//Image转换Bitmap
        //1. Bitmap img = new Bitmap(imgSelect.Image);
        //2. Bitmap bmp = (Bitmap)pictureBox1.Image;

        /// &lt;summary&gt;
        /// 将图片Image转换成Byte[]
        /// &lt;/summary&gt;
        /// &lt;param name="Image"&gt;image对象&lt;/param&gt;
        /// &lt;param name="imageFormat"&gt;后缀名&lt;/param&gt;
        /// &lt;returns&gt;&lt;/returns&gt;
        public static byte[] ImageToBytes(Image Image, System.Drawing.Imaging.ImageFormat imageFormat)
        {
            if (Image == null) { return null; }
            byte[] data = null;
            using (MemoryStream ms = new MemoryStream())
            {
                using (Bitmap Bitmap = new Bitmap(Image))
                {
                    Bitmap.Save(ms, imageFormat);
                    ms.Position = 0;
                    data = new byte[ms.Length];
                    ms.Read(data, 0, Convert.ToInt32(ms.Length));
                    ms.Flush();
                }
            }
            return data;
        }

        /// &lt;summary&gt;
        /// byte[]转换成Image
        /// &lt;/summary&gt;
        /// &lt;param name="byteArrayIn"&gt;二进制图片流&lt;/param&gt;
        /// &lt;returns&gt;Image&lt;/returns&gt;
        public static System.Drawing.Image byteArrayToImage(byte[] byteArrayIn)
        {
            if (byteArrayIn == null)
                return null;
            using (System.IO.MemoryStream ms = new System.IO.MemoryStream(byteArrayIn))
            {
                System.Drawing.Image returnImage = System.Drawing.Image.FromStream(ms);
                ms.Flush();
                return returnImage;
            }
        }

        /// &lt;summary&gt;
        /// byte[] 转换 Bitmap
        /// &lt;/summary&gt;
        /// &lt;param name="Bytes"&gt;byte[]&lt;/param&gt;
        /// &lt;returns&gt;&lt;/returns&gt;
        public static Bitmap BytesToBitmap(byte[] Bytes)
        {
            MemoryStream stream = null;
            try
            {
                stream = new MemoryStream(Bytes);
                return new Bitmap((Image)new Bitmap(stream));
            }
            catch (ArgumentNullException ex)
            {
                throw ex;
            }
            catch (ArgumentException ex)
            {
                throw ex;
            }
            finally
            {
                stream.Close();
            }
        }

        /// &lt;summary&gt;
        /// Bitmap转byte[]  
        /// &lt;/summary&gt;
        /// &lt;param name="Bitmap"&gt;Bitmap&lt;/param&gt;
        /// &lt;returns&gt;&lt;/returns&gt;
        public static byte[] BitmapToBytes(Bitmap Bitmap)
        {
            MemoryStream ms = null;
            try
            {
                ms = new MemoryStream();
                Bitmap.Save(ms, Bitmap.RawFormat);
                byte[] byteImage = new Byte[ms.Length];
                byteImage = ms.ToArray();
                return byteImage;
            }
            catch (ArgumentNullException ex)
            {
                throw ex;
            }
            finally
            {
                ms.Close();
            }
        }
</pre>
</div>
<p>&nbsp;</p>