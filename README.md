<html>
<head>
<meta name=viewport content=width=device-width; >
<style>
.InThisEnd {
background:red;
}
.NotInThisEnd {
background:grey;
}
</style>
</head>
<script>
var myVar=setInterval(function(){IncramentElapseTimer()},1000);
var vPlayingInEnd="Nothing";
var vClockRunning="Yes";
var vSecondsInLeftEnd=0;
var vSecondsInNeutralEnd=0;
var vSecondsInRightEnd=0;
function onLoadFunction() {

}
function IncramentElapseTimer() {
if (vClockRunning=="Yes") {
    if (vPlayingInEnd=="Left") {vSecondsInLeftEnd=vSecondsInLeftEnd+1;}
    if (vPlayingInEnd=="Neutral") {vSecondsInNeutralEnd=vSecondsInNeutralEnd+1;}
    if (vPlayingInEnd=="Right") {vSecondsInRightEnd=vSecondsInRightEnd+1;}
   }
UpdateDisplay();
}
function ChangePlayTo(vThisEnd) {
vPlayingInEnd=vThisEnd;
document.getElementById("LeftEnd").className = "NotInThisEnd";
document.getElementById("Neutral").className = "NotInThisEnd";
document.getElementById("RightEnd").className = "NotInThisEnd";
if (vThisEnd=='Left')
   {document.getElementById("LeftEnd").className = "InThisEnd";}
if (vThisEnd=='Neutral')
   {document.getElementById("Neutral").className = "InThisEnd";}
if (vThisEnd=='Right')
   {document.getElementById("RightEnd").className = "InThisEnd";}
}
function UpdateDisplay(vThisEnd) {
document.getElementById("TotalTimeLeft").innerHTML=toHHMMSS(vSecondsInLeftEnd);
document.getElementById("TotalTimeNeutral").innerHTML=toHHMMSS(vSecondsInNeutralEnd);
document.getElementById("TotalTimeRight").innerHTML=toHHMMSS(vSecondsInRightEnd);
}
function SendEMail() {
var subject= "Interesting Information";
var body = "";
body += vSecondsInLeftEnd;

var uri = "mailto:?subject=";
uri += encodeURIComponent(subject);
uri += "&body=";
uri += encodeURIComponent(body);
window.open(uri);
}
function toHHMMSS(iNumSeconds) {
    var sec_num = parseInt(iNumSeconds, 10); // don't forget the second parm
    var hours   = Math.floor(sec_num / 3600);
    var minutes = Math.floor((sec_num - (hours * 3600)) / 60);
    var seconds = sec_num - (hours * 3600) - (minutes * 60);

    if (hours   < 10) {hours   = "0"+hours;}
    if (minutes < 10) {minutes = "0"+minutes;}
    if (seconds < 10) {seconds = "0"+seconds;}
    var time    = hours+':'+minutes+':'+seconds;
    return time;
}
</script>
<body onload="onLoadFunction();">
<table width="280" border=1>
  <col width="140">
  <col width="140">
  <col width="140">
<tr><td>This Game</td></tr>
<tr>
<td><input type="submit" id="LeftEnd"  value="Left End"  class="NotInThisEnd" style="width:200px;height:500px" onclick="ChangePlayTo('Left')" /></td>
<td><input type="submit" id="Neutral"  value="Neutral"   class="InThisEnd"    style="width:200px;height:500px" onclick="ChangePlayTo('Neutral')" /></td>
<td><input type="submit" id="RightEnd" value="Right End" class="NotInThisEnd" style="width:200px;height:500px" onclick="ChangePlayTo('Right')" /></td>
</tr>
<tr>
<td><span id=TotalTimeLeft>0</span></td>
<td><span id=TotalTimeNeutral>0</span></td>
<td><span id=TotalTimeRight>0</span></td></tr>
</table>

<input type="submit" id="" value="Send"   onclick="SendEMail()" />

</body>
</html>
