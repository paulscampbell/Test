<table width="280" border=1>
  <col width="140">
  <col width="140">
  <col width="140">
<tr><td>This Game</td></tr>
<tr>
<td><input type="submit" id="LeftEnd"  value="Left End"  style="width:200px;height:500px" onclick="ChangePlayTo('Left')" /></td>
<td><input type="submit" id="Neutral"  value="Neutral"      style="width:200px;height:500px" onclick="ChangePlayTo('Neutral')" /></td>
<td><input type="submit" id="RightEnd" value="Right End"  style="width:200px;height:500px" onclick="ChangePlayTo('Right')" /></td>
</tr>
<tr>
<td><span id=TotalTimeLeft>0</span></td>
<td><span id=TotalTimeNeutral>0</span></td>
<td><span id=TotalTimeRight>0</span></td></tr>
</table>

<input type="submit" id="" value="Send"   onclick="SendEMail()" />

