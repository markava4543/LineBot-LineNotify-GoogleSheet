# LineBot-LineNotify-GoogleSheet

 function doPost(e) {
  var ssId = "<Your Sheet ID>";
  var ss = SpreadsheetApp.openById("Your Sheet ID");
  SpreadsheetApp.setActiveSpreadsheet(ss);
  var sheetData1 = ss.getSheetByName("SHEET NAME");
  //use BetterLog
  Logger = BetterLog.useSpreadsheet("Your Sheet ID");
  //Logger.log("Hello from BetterLog 🙂");
  var queryText = e.postData.contents;
  const json= JSON.parse(queryText);
  const message = json.queryResult.queryText;
  Logger.log(message);
  sendMessageToLineNotify(message);
}
function sendMessageToLineNotify(message, accesssToken) {
  const lineNotifyEndPoint = "https://notify-api.line.me/api/notify";
  const accessToken = "AccessToken";
  var options =
  {
    "method"  : "post",
    "payload" : "message=" + message,
    "headers" : {"Authorization" : "Bearer "+ accessToken}
 };
UrlFetchApp.fetch("https://notify-api.line.me/api/notify",options);
  
  
  
  // Edit on ssId,ss,sheetData1,AccessToken
