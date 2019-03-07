# jsonp
Jsonp('https://suggest.taobao.com/sug',{q:'fang',callback:'callbk'})
      function Jsonp(url, obj) {
        let arr = Object.entries(obj); //把数组切割成为二维数组
        var str = "";
        arr.some((item, index, arr) => {
          //数据序列化
          if (index != arr.length - 1) {
            str += item[0] + "=" + item[1] + "&";
          } else {
            str += item[0] + "=" + item[1];
          }
        }); //
        console.log(str);
        let script = document.createElement("script"); //新建一个script标签
        script.id = "script";
        script.src = `${url}?${str}`; // console.log(script.src);
        document.body.appendChild(script); //删除多余的元素，只是为了拿到内容而已
        if (document.querySelector("#script")) {
          document.body.removeChild(document.querySelector("#script"));
        }
      }
