# reduceLeadsByEmail
function validateEmail(email) {<br>
    var re = /^([\w-]+(?:\.[\w-]+)*)@((?:[\w-]+\.)*\w[\w-]{0,66})\.([a-z]{2,6}(?:\.[a-z]{2})?)$/i;<br>
    return re.test(email);<br>
}<br><br>

function reduceLeadsByEmail(dataEmails){<br>
  var result = [];<br>
  _.each(dataEmails,function(lead1){<br>
    if(!validateEmail(lead1))<br>
         return;<br>
    if(result.length === 0){<br>
       result.push(lead1);<br>
       return;<br>
    }<br>
    var v = _.find(result, function(num){ return num === lead1; });<br>
    if(_.isUndefined(v))<br>
      result.push(lead1);<br>
  });<br>
  console.log(result);<br>
}<br><br>

var data = ["01@gmail.com", "02@gmail.com", "03@gmail.com", "01@gmail.com"];<br>
reduceLeadsByEmail(data);<br><br>

var data = ["01@gmail.com", "01@gmail.com", "01@gmail.com", "01@gmail.com"];<br>
reduceLeadsByEmail(data);<br><br>

var data = [];<br>
reduceLeadsByEmail(data);<br><br>

var data = ["01", "01@gmail.com"];<br>
reduceLeadsByEmail(data);<br><br>

var data = ["01", "02"];<br>
reduceLeadsByEmail(data);<br><br>

var data = [null, undefined];<br>
reduceLeadsByEmail(data);
