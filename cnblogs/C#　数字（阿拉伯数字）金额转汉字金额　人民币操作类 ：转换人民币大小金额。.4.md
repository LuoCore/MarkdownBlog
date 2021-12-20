<div class="cnblogs_Highlighter">
<pre class="brush:csharp;gutter:true;">  /// &lt;summary&gt;
        /// 转换为人民币大写金额形式
        /// &lt;/summary&gt;
        /// &lt;param name="Money"&gt;金额&lt;/param&gt;
        /// &lt;returns&gt;返回大写形式&lt;/returns&gt;
        public static string NumberToChineseMoney(this object number)
        {
            decimal numberMoney = 0;
            try
            {
                numberMoney = Convert.ToDecimal(number);
            }
            catch
            {
                return "非数字形式！";
            }
            //0-9数字所对应的汉字
            const string numericChinese = "零壹贰叁肆伍陆柒捌玖";
            //数字单位所对应的汉字
            string unitChinese = "万仟佰拾亿仟佰拾万仟佰拾元角分";
            //将Money取绝对值并四舍五入取2位小数
            numberMoney = Math.Round(Math.Abs(numberMoney), 2);
            //数字的字符串形式
            string strNumeric = ((long)(numberMoney * 100)).ToString();
            //人民币大写金额形式
            string strCmycurD = "";
            //最高单位
            int maxUnit = strNumeric.Length;    
            if (maxUnit &gt; 15) { return "溢出"; }
            //取出对应位数的unitChinese的值。如：200.55,maxUnit为5所以unitChinese=佰拾元角分
            unitChinese = unitChinese.Substring(15 - maxUnit);
            //数字单位的汉字转换
            string unitConvert = "";
            //用来计算连续的零值是几个
            int nzero = 0; 
            //循环取出每一位需要转换的值
            for (int i = 0; i &lt; maxUnit; i++)
            {
                //数字的汉字转换
                string numericConvert;
                //取出需转换的某一位的值
                string strConvertValue = strNumeric.Substring(i, 1);
                //转换为数字
                int convertValue = Convert.ToInt32(strConvertValue);    
                if (i != (maxUnit - 3) &amp;&amp; i != (maxUnit - 7) &amp;&amp; i != (maxUnit - 11) &amp;&amp; i != (maxUnit - 15))
                {
                    //当所取位数不为元、万、亿、万亿上的数字时
                    if (strConvertValue == "0")
                    {
                        numericConvert = "";
                        unitConvert = "";
                        nzero = nzero + 1;
                    }
                    else
                    {
                        if (strConvertValue != "0" &amp;&amp; nzero != 0)
                        {
                            numericConvert = "零" + numericChinese.Substring(convertValue * 1, 1);
                            unitConvert = unitChinese.Substring(i, 1);
                            nzero = 0;
                        }
                        else
                        {
                            numericConvert = numericChinese.Substring(convertValue * 1, 1);
                            unitConvert = unitChinese.Substring(i, 1);
                            nzero = 0;
                        }
                    }
                }
                else
                {
                    //该位是万亿，亿，万，元位等关键位
                    if (strConvertValue != "0" &amp;&amp; nzero != 0)
                    {
                        numericConvert = "零" + numericChinese.Substring(convertValue * 1, 1);
                        unitConvert = unitChinese.Substring(i, 1);
                        nzero = 0;
                    }
                    else
                    {
                        if (strConvertValue != "0" &amp;&amp; nzero == 0)
                        {
                            numericConvert = numericChinese.Substring(convertValue * 1, 1);
                            unitConvert = unitChinese.Substring(i, 1);
                            nzero = 0;
                        }
                        else
                        {
                            if (strConvertValue == "0" &amp;&amp; nzero &gt;= 3)
                            {
                                numericConvert = "";
                                unitConvert = "";
                                nzero = nzero + 1;
                            }
                            else
                            {
                                if (maxUnit &gt;= 11)
                                {
                                    numericConvert = "";
                                    nzero = nzero + 1;
                                }
                                else
                                {
                                    numericConvert = "";
                                    unitConvert = unitChinese.Substring(i, 1);
                                    nzero = nzero + 1;
                                }
                            }
                        }
                    }
                }
                if (i == (maxUnit - 11) || i == (maxUnit - 3))
                {
                    //如果该位是亿位或元位，则必须写上
                    unitConvert = unitChinese.Substring(i, 1);
                }
                strCmycurD = strCmycurD + numericConvert + unitConvert;

                if (i == maxUnit - 1 &amp;&amp; strConvertValue == "0")
                {
                    //最后一位（分）为0时，加上&ldquo;整&rdquo;
                    strCmycurD = strCmycurD + '整';
                }
            }
            if (numberMoney == 0)
            {
                strCmycurD = "零元整";
            }
            return strCmycurD;
        }
</pre>
</div>
<p>&nbsp;</p>