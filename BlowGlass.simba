program AutoSuperGlass;

{$DEFINE SMART8}
{$I SRL-OSR/SRL.Simba}

Const
  Version = '1.0';
  NumPlayers = 1;
  StartPlayer = 0;

var
  Scount, BankX, BankY, Wx, Wy ,x,y: integer;

procedure DeclareVariables;
begin
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
  MakeCompass('W');
end;

procedure ExitScreen;
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

procedure WithdrawGlass;
begin
  wait(randomrange(40,60));
  MMouse(95,79,4,4);
  wait(randomrange(30,40));
  clickmouse2(mouse_right);
  wait(randomrange(40,50));
  ChooseOptionMulti(['ll']);
  wait(randomrange(20,30));
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

procedure Bankorb;
begin
  if FindColorTolerance(Wx, Wy, 15066600, 550, 203, 733, 460, 10) then
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
      if FindObjCustom(BankX, BankY, ['ank boot','nk boo', 'k boot'], [5665662,9610936], 5) then
      begin
        wait(randomrange(50,100));
        MMouse(BankX, BankY, 2, 2);
        wait(randomrange(100,150));
        clickmouse2(mouse_left);

        repeat
          wait(randomrange(100,120));
          BankScreenCount := BankScreenCount + 1;
          writeln(IntToStr(BankScreenCount));
        until ((FindColorTolerance(x, y, 2070783, 248, 30, 288, 50, 10)) or (BankScreenCount = 10))

        if (FindColorTolerance(x, y, 2070783, 248, 30, 288, 50, 10)) then
        begin
          Found := true;

          BankOrb;
          WithdrawGlass;

          ExitScreen;
        end;

        wait(randomrange(75,100));
        if (not FindColorTolerance(x, y, 2070783, 248, 30, 288, 50, 10)) then
          break;
      end;
      if (FindColorTolerance(x, y, 2070783, 248, 30, 288, 50, 10)) then
        ExitScreen;
      wait(RandomRange(200,300));
    until (Found)
    if (Found = true) then
      break;
    wait(randomrange(30,40));
  until (Outloop = 4)
end;

procedure BlowGlass;
begin
  if (FindColorTolerance(x, y, 7763583, 558,212, 594, 240, 10)) then
  begin
    MMouse(x, y, 3, 3);
    wait(randomrange(200,250));
    clickmouse2(mouse_left);
    wait(randomrange(50,100));
    MMouse(619, 230, 3, 3);
    wait(randomrange(50,100));
    clickmouse2(mouse_left);
    wait(randomrange(1500,1540));

    if (FindColorTolerance(x, y, 39423, 248, 30, 288, 50, 10)) then
    begin
      wait(randomrange(100,150));
      MMouse(210,210, 3, 3);
      wait(randomrange(200,300));
      clickmouse2(mouse_right);
      wait(randomrange(50,100));
      if ChooseOptionMulti(['X', 'e X']) then
      begin
        wait(randomrange(950,900));
        if (not FindColorTolerance(x, y, 0, 49,372, 103,417, 5)) then
          TypeSendEx('33', true);

        repeat
          wait(randomrange(3000,4000));

          if (FindColorTolerance (x, y, 8388608, 256, 373, 353, 397, 1)) then
          begin
            MMouse(292, 446, 5, 2);
            wait(randomrange(600,650));
            clickmouse2(mouse_left);
            break;
          end;
        until (not FindColorTolerance (x, y, 1404856, 557, 213, 728, 462, 10))
      end;
    end;
  end;
end;


//START AT CHARTER
//TPOINTARRAY AT MINIMAP TAKE SECOND MOST COMMON COLOR.

procedure antiBan;
begin
  Case Random(50) Of
    1:
      begin
        Boredhuman;
        MakeCompass('W');
      end;
    2: Wait(2500 + random(4500));
    3: PickUpMouse;
    4: RandomRClick;
    5:
      begin
        Boredhuman;
        MakeCompass('W');
      end;
    6:
      begin
        Boredhuman;
        MakeCompass('W');
      end;
  end;
end;


Begin
  SMART_FIXSPEED := TRUE;
  SetupSRL;
  DeclarePlayers;
  StartUp;
  Scount := 0;
  GameTab(tab_Inv);

  repeat
    Bank;
    BlowGlass;
    Antiban;
    if (not GameTab(tab_Inv)) then
      GameTab(tab_Inv);
  until (0 = 1)
End.








