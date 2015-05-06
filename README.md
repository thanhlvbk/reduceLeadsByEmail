# reduceLeadsByEmail
function validateEmail(email) {<br>
    var re = /^([\w-]+(?:\.[\w-]+)*)@((?:[\w-]+\.)*\w[\w-]{0,66})\.([a-z]{2,6}(?:\.[a-z]{2})?)$/i;
    return re.test(email);
}

function reduceLeadsByEmail(dataEmails){
  var result = [];
  _.each(dataEmails,function(lead1){
    if(!validateEmail(lead1))
         return;
    if(result.length === 0){
       result.push(lead1);
       return;
    }
    var v = _.find(result, function(num){ return num === lead1; });
    if(_.isUndefined(v))
      result.push(lead1);
  });
  console.log(result);
}

var data = ["01@gmail.com", "02@gmail.com", "03@gmail.com", "01@gmail.com"];
reduceLeadsByEmail(data);

var data = ["01@gmail.com", "01@gmail.com", "01@gmail.com", "01@gmail.com"];
reduceLeadsByEmail(data);

var data = [];
reduceLeadsByEmail(data);

var data = ["01", "01@gmail.com"];
reduceLeadsByEmail(data);

var data = ["01", "02"];
reduceLeadsByEmail(data);

var data = [null, undefined];
reduceLeadsByEmail(data);
