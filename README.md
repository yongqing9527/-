# 数组对象
* 封装slice()

      function sliceArray(array, size) {
        var result = [];
        for (var x = 0; x < Math.ceil(array.length / size); x++) {
            var start = x * size;
            var end = start + size;
            result.push(array.slice(start, end));
        }
        return result;
      }   
      var array = [1,2,3,4,5,6,7,8,9];
      var array = sliceArray(array, 4);
      console.log(array);
# 用js实现table内容从下到上连续滚动

      //html代码
      <div id="table" style="overflow: hidden; height: 240px;">
          <div id="table1">
              <table width="600" border="0" align="center" cellpadding="0" cellspacing="0" bordercolor="4FBFF9">
                  <tr>
                      <td width="120" align="center">201404020001</td>
                      <td width="130">测试业务</td>
                      <td width="150">申请企业名称</td>
                      <td width="100" align="center">2014-03-13</td>
                      <td width="100" align="center">在办</td>
                  </tr>
              </table>
          </div>
          <div id="table2"></div>
      </div>
      //js代码
      function tablemove(speed) {
          var table = document.querySelector('#table');
          var table1 = document.querySelector('#table1');
          var table2 = document.querySelector('#table2');
          table2.innerHTML = table1.innerHTML;
          function Marquee() {
              if (table2.offsetTop - table.scrollTop <= 0) {
                  table.scrollTop -= table1.offsetHeight;
              } else {
                  table.scrollTop++;
              }
          }
          var MyMar = setInterval(Marquee, speed);
          table.onmouseover = function() {
              clearInterval(MyMar);
          };
          table.onmouseout = function() {
              MyMar = setInterval(Marquee, speed);
          }
      }
