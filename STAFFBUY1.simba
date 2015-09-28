//Hsxu's AutoBuyer: Version 1.1 - LundailBuy
//Version 1.0: Coordinate detection
//             Buys runs until out of stock
//
//Version 1.1: Replacing coordinate clicks with color detection.
//             MMouse functions have been cleaned up of RandomRanges, using 3rd and 4th parameters instead
//             More code has been changed to color timed instead of random timed
program AutoBuy;

{$DEFINE SMART8}
{$I SRL-OSR/SRL.Simba}

Const
  Version = '1.0';
  NumPlayers = 1;
  StartPlayer = 0;

var
  wizx, wizy, Scount, WorldCount, BankX, BankY, Wx, Wy, GroundColor,x,y, Trips: integer;
  IsPlayerLogged: Boolean;

procedure DeclareVariables;
begin
  WorldCount := 9;
end;

Procedure DeclarePlayers;
begin
  HowManyPlayers := 1;
  NumberOfPlayers(HowManyPlayers);
  CurrentPlayer := 0;
  with Players[0] do
  begin
    Name        := '';    //RSN
    Pass        := '';    //Pass
    Active      := True;
  end;
end;

procedure StartUp;
begin
  ClearDebug;
  DeclareVariables;
  if (not LoggedIn) then
    LogInPlayer();
  SetAngle(SRL_ANGLE_HIGH);
end;

procedure Trade;
begin
  clickmouse2(mouse_right);
  wait(randomrange(150,200));
  if (ChooseOptionMulti(['rade Ma', 'ade Ma', 'e Ma'])) then
  begin
    wait(randomrange(750,1000));
  end;
end;

procedure ExitTradeScreen;
var
  x, y: integer;
begin
  repeat
    wait(RandomRange(400,500));
    MMouse(485, 41, 5, 5);
    wait(RandomRange(400,500));
    if (FindColorTolerance(x, y, 65536, 480, 36, 490, 46, 10)) then
      clickmouse2(mouse_left);
    wait(RandomRange(100,150));
  until (not FindColorTolerance(x, y, 65536, 480, 36, 490, 46, 10))
end;

procedure BuyBS;
begin
  MMouse(279, 132, 3, 1);
  wait(RandomRange(60,65));
  clickmouse2(mouse_right);
  wait(RandomRange(20,30));
  MMouse(279, 204, 2, 1);
  wait(RandomRange(20,30));
  clickmouse2(mouse_left);
end;

procedure BuySlotSeven;
begin
  MMouse(377, 84, 3, 1);
  wait(RandomRange(30,32));
  clickmouse2(mouse_right);
  wait(RandomRange(9,12));
  MMouse(377, 157, 3, 1);
  wait(RandomRange(9,12));
  clickmouse2(mouse_left);
  wait(RandomRange(9,12));
end;

procedure BuySlotNine;
begin
  MMouse(95, 131, 3, 1);
  wait(RandomRange(30,32));
  clickmouse2(mouse_right);
  wait(RandomRange(9,12));
  MMouse(91, 204, 3, 1);
  wait(RandomRange(9,12));
  clickmouse2(mouse_left);
  wait(RandomRange(9,12));
end;

procedure BuySlotEight;
begin
  MMouse(425, 83, 3, 1);
  wait(RandomRange(30,32));
  clickmouse2(mouse_right);
  wait(RandomRange(9,12));
  MMouse(425, 157, 3, 1);
  wait(RandomRange(9,12));
  clickmouse2(mouse_left);
  wait(RandomRange(9,12));
end;

procedure BuyObject;
var
  X, Y, a ,b ,c, TradeScreenCount, Outerloop: integer;
  Found: boolean;
begin
  Found := false;

  repeat
    TradeScreenCount := 0;
    repeat
      if (FindObjCustom(wizX,wizY, ['agic','ic St'], [5584904, 6833160,9724177], 10)) Then
      begin
        a := 0;
        b := 0;
        c := 0;
        Outerloop := Outerloop + 1;
        Trade;

        repeat
          wait(randomrange(100,120));
          TradeScreenCount := TradeScreenCount + 1;
          writeln(IntToStr(TradeScreenCount));
        until ((FindColorTolerance(x, y, 2070783, 248, 30, 288, 50, 10)) or (TradeScreenCount = 60))

        if (FindColorTolerance(x, y, 2070783, 248, 30, 288, 50, 10)) then
        begin
          Found := true;

          BuyBS;

          //repeat
            //BuySlotEight;
            //c := c + 1;
          //until ((c = 25) or (not FindColorTolerance(x, y, 65535, 416, 71, 427, 80, 50)) and (not FindColorTolerance(x, y, 1679011, 416, 71, 427, 80, 50)))

          (*repeat
            BuySlotSeven;
            a := a + 1;
          until ((a = 3) or (not FindColorTolerance(x, y, 65535, 372, 72, 380, 80, 10)) and (not FindColorTolerance(x, y, 1679011, 372, 72, 380, 80, 10)))

          repeat
            BuySlotNine;
            b := b + 1;
          until ((b = 3) or (not FindColorTolerance(x, y, 65535, 88, 120, 98, 130, 50)) and (not FindColorTolerance(x, y, 1679011, 88, 120, 98, 130, 50)))
          *)
          ExitTradeScreen;
        end;

        wait(randomrange(75,100));
        if (not FindColorTolerance(x, y, 2070783, 248, 30, 288, 50, 10)) then
          break;
      end;
      if (FindColorTolerance(x, y, 2070783, 248, 30, 288, 50, 10)) then
        ExitTradeScreen;
      wait(RandomRange(200,300));
    until(Found = true)
    if (Found = true) then
      break;
  until(Outerloop = 4)
end;

procedure LogPlayerOut;
begin
  MMouse(643, 484, 5, 5);
  wait(randomrange(1000, 1200));
  clickmouse2(mouse_left);
  MMouse(640, 375, 20, 5);
  wait(randomrange(500, 1000));
  clickmouse2(mouse_left);
  wait(randomrange(200, 300));
end;

procedure HopWorld;
var
  x, y: integer;
begin
  repeat
    wait(randomrange(500, 600));
    MMouse(52, 479, 38, 8);
    clickmouse2(mouse_left);
    wait(randomrange(200,300));
  until(FindColorTolerance(x, y, 0, 105, 385, 110, 390, 2))

  wait(RandomRange(700,800));

  if (WorldCount < 6) then
    MMouse(235, (248 + WorldCount*24), 20, 1);
  if ((WorldCount = 6) or (WorldCount = 7)) then
    MMouse(235, (272 + WorldCount*24), 20, 1);
  if ((WorldCount >= 8) and (WorldCount <= 23)) then
    MMouse(335, (85 + (WorldCount-8)*24), 20, 1);
  if ((WorldCount >= 24) and (WorldCount <= 39)) then
    MMouse(425, (85 + (WorldCount-24)*24), 20, 1);
  if ((WorldCount >= 40) and (WorldCount <= 53)) then
    MMouse(525, (85 + (WorldCount-40)*24), 20, 1);

  if (WorldCount = 15) then
    WorldCount := 9;

  wait(RandomRange(700, 800));
  ClickMouse2(mouse_left);
  wait(RandomRange(100, 200));
  WorldCount := WorldCount + 1;
end;

procedure BankRunes;
begin
  repeat
    if FindColorTolerance(Wx, Wy, 8750479,550, 203, 733, 460, 10) then
    begin
      wait(randomrange(20,30));
      MMouse(Wx, Wy, 1, 1);
      wait(randomrange(40,50));
      clickmouse2(mouse_right);
      wait(randomrange(40,50));
      if ChooseOptionMulti(['ll']) then
      begin
        wait(randomrange(200,300));
      end;
      wait(randomrange(40,50));
    end;
  until (not FindColorTolerance(Wx, Wy, 8750479,550, 203, 733, 460, 10))
end;

procedure BankBS;
begin
  repeat
    if FindColorTolerance(Wx, Wy, 1207955,550, 203, 733, 460, 10) then
    begin
      wait(randomrange(20,30));
      MMouse(Wx, Wy, 1, 1);
      wait(randomrange(40,50));
      clickmouse2(mouse_right);
      wait(randomrange(40,50));
      if ChooseOptionMulti(['ll']) then
      begin
        wait(randomrange(200,300));
      end;
      wait(randomrange(40,50));
    end;
  until (not FindColorTolerance(Wx, Wy, 1207955,550, 203, 733, 460, 10))
end;

procedure BankCash;
begin
  repeat
    if FindColorTolerance(Wx, Wy, 2014696,550, 203, 733, 460, 10) then
    begin
      wait(randomrange(20,30));
      MMouse(Wx, Wy, 1, 1);
      wait(randomrange(40,50));
      clickmouse2(mouse_right);
      wait(randomrange(40,50));
      if ChooseOptionMulti(['ll']) then
      begin
        wait(randomrange(200,300));
      end;
      wait(randomrange(40,50));
    end;
  until (not FindColorTolerance(Wx, Wy, 2014696,550, 203, 733, 460, 10))
end;

procedure WithdrawCash;
begin
  wait(randomrange(200,300));
  MMouse(94,75, 3, 3);
  wait(randomrange(500,600));
  clickmouse2(mouse_right);
  wait(randomrange(100,200));
  if (ChooseOptionMulti(['X', 'aw X'])) then
  begin
    wait(randomrange(900,950));
    if (not FindColorTolerance (x, y, 0, 49, 372, 103, 417, 5)) then
    begin
      TypeSendEx('300000', true);
      wait(randomrange(500,600));
    end;
  end;
end;

procedure Bank;
var
  x, y, BankScreenCount, Outloop: integer;
  Found: boolean;
begin
  Found := False;
  repeat
    BankScreenCount := 0;
    repeat
      if FindObjCustom(BankX, BankY, ['ank boot','nk boo', 'k boot'], [7509414, 607580], 10) then
      begin
        wait(randomrange(50,100));
        MMouse(BankX, BankY, 2, 2);
        wait(randomrange(100,150));
        clickmouse2(mouse_left)

        repeat
          wait(randomrange(100,120));
          BankScreenCount := BankScreenCount + 1;
          writeln(IntToStr(BankScreenCount));
        until ((FindColorTolerance(x, y, 2070783, 248, 30, 288, 50, 10)) or (BankScreenCount = 50))


        if (FindColorTolerance(x, y, 2070783, 248, 30, 288, 50, 10)) then
        begin

          Found := true;

          BankRunes;
          BankBS;
          BankCash;

          WithdrawCash;

          ExitTradeScreen;
        end;

        wait(randomrange(75,100));
        if (not FindColorTolerance(x, y, 2070783, 248, 30, 288, 50, 10)) then
          break;
      end;
      if (FindColorTolerance(x, y, 2070783, 248, 30, 288, 50, 10)) then
        ExitTradeScreen;
      wait(RandomRange(200,300));
    until (Found)
    if (Found = true) then
      break;
    wait(randomrange(30,40));
  until (Outloop = 4)
end;


procedure WalkDownstairs;
var
  Done: boolean;
begin
  writeln('Walking downstairs to Wiz Guild lobby');
  Done := false;
  MMouse(643, 36, 4, 1);
  wait(randomrange(400,500));
  clickmouse2(mouse_left);
  wait(randomrange(2500,2700));

  repeat
    if (FindObj(x, y, 'b-d', 541274 , 5)) then
    begin
      Mmouse(x, y, 0, 0);
      wait(randomrange(600,700));
      clickmouse2(mouse_right);
      if (ChooseOptionMulti(['b-d'])) then
      begin
        Done := true;
        wait(randomrange(500,600));
      end;
    end;
    wait(randomrange(100,200));
  until (Done)
  wait(randomrange(1500,1600));
end;

procedure WalkOutsideGuild;
var
  Done: boolean;

begin
  writeln('Walking outside Wiz Guild');
  Done := false;
  MMouse(694, 84, 1, 2);
  wait(randomrange(400,500));
  clickmouse2(mouse_left);
  wait(randomrange(1500,1700));
  repeat
    if (FindObjCustom(x, y, ['en', 'ic', 'ld'], [3231083, 3099239, 2439761, 4817567, 4289420], 3)) then
    begin
      MMouse(x, y, 0, 0);
      wait(randomrange(600,700));
      clickmouse2(mouse_right);
      if (ChooseOptionMulti(['pen Mag', 'en Mag'])) then
      begin
        Done := true;
        wait(randomrange(1500,1600));
      end;
    end;
    wait(randomrange(100,200));
  until(Done)
end;



  //writeln('Walking to top of dock from charter');
  //RadialWalkTolerance(DockID , 45, -45, 75, 0, 1, 15);
  //writeln('Walking to bank');
  //RadialWalkTolerance(8157830, 0, 60, 55, -1, 1, 25);

procedure WalkToBank;
var
  Hit: boolean;
begin
  Groundcolor := GetColor(647, 83);
  Hit := false;

  writeln('Walking to Bank');
  RadialRoadWalk(GroundColor, 75, 105, 30, -1, 0);
  Hit := RadialWalkTolerance(9802912, 50, 130, 40, -1, 0, 20);
  if (not Hit) then
    Hit := RadialWalkTolerance(8684686, 50, 130, 40, -1, 0, 20);
      if (not Hit) then
        Hit := RadialWalkTolerance(7105655, 50, 130, 40, -1, 0, 20);
end;

procedure WalkToGuild;
var
  Hit: boolean;
begin
  Hit := false;
  writeln('Walking back to Guild');
  RadialRoadWalk(GroundColor, 280, 260, 30, 1, 0);
  Hit := RadialWalkTolerance(233, 280, 180, 70, 1, 0, 20);
  wait(randomrange(600,700));
end;

procedure WalkInsideGuild;
var
  Done: boolean;

begin
  writeln('Walking inside Wiz Guild');
  Done := false;
  //MMouse(654, 84, 1, 2);
  //wait(randomrange(400,500));
  //clickmouse2(mouse_left);
  //wait(randomrange(1500,1700));
  repeat
    if (FindObjCustom(x, y, ['en', 'ic', 'ld'], [1812704, 2703448, 3362926, 1327959], 3)) then
    begin
      MMouse(x, y, 0, 0);
      wait(randomrange(600,700));
      clickmouse2(mouse_right);
      if (ChooseOptionMulti(['pen Mag', 'en Mag'])) then
      begin
        Done := true;
        wait(randomrange(1500,1600));
      end;
    end;
    wait(randomrange(100,200));
  until(Done)
  wait(randomrange(1500,1600));
end;

procedure WalkUpStairs;
var
  Done: boolean;

begin
  writeln('Walking Upstairs');
  repeat
    if (FindObjCustom(x, y, ['b-u', 'up', 'ase'],[605778, 12611], 10)) then
    begin
      Mmouse(x, y, 0, 0);
      wait(randomrange(600,700));
      clickmouse2(mouse_right);
      if (ChooseOptionMulti(['b-u'])) then
      begin
        Done := true;
        wait(randomrange(500,600));
      end;
    end;
    wait(randomrange(100,200));
  until (Done)
  wait(randomrange(3500,3600));
  MMouse(677,93,1,1);
  wait(randomrange(500,600));
  clickmouse2(mouse_left);
  wait(randomrange(1500,1600));
end;

//START AT CHARTER
//TPOINTARRAY AT MINIMAP TAKE SECOND MOST COMMON COLOR.

Begin
  SMART_FIXSPEED := TRUE;
  SetupSRL;
  DeclarePlayers;
  StartUp;
  Scount := 0;

  repeat
    BuyObject;

    if (InvFull) then
    begin
      RunEnergy(50);
      WalkDownstairs;
      WalkOutsideGuild;
      WalkToBank;
      Bank;
      WalkToGuild;
      WalkInsideGuild;
      WalkUpstairs;
      BuyObject;
    end;

    Trips := Trips + 1;
    writeln('Total Trips');
    writeln(IntToStr(Trips));

    repeat
      Logout();
    until(not LoggedIn)

    HopWorld;
    LoginPlayer();
  until (0 = 1)
End.








