program AutoSuperGlass;

{$DEFINE SMART8}
{$I SRL-OSR/SRL.Simba}

Const
  Version = '1.0';
  NumPlayers = 1;
  StartPlayer = 0;

var
  Scount, BstaankX, BankY, Wx, Wy, z, Alchamt: integer;

procedure DeclareVariables;
begin
  Alchamt := 9999;
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

procedure AutoAlch;
begin
  wait(randomrange(2400,2410));
  clickmouse2(mouse_left);
  wait(randomrange(30,40));
  clickmouse2(mouse_left);
end;


//START AT CHARTER
//TPOINTARRAY AT MINIMAP TAKE SECOND MOST COMMON COLOR.

procedure antiBan;
begin
  Case Random(1000) Of
    1:
      begin
        Boredhuman;
        MakeCompass('W');
        GameTab(tab_Magic);
        Mmouse(710, 335, 2, 2);
      end;
    2:
      begin
        Wait(2500 + random(4500));
        GameTab(tab_Magic);
        Mmouse(710, 335, 2, 2);
      end;
    3:
      begin
      PickUpMouse;
      GameTab(tab_Magic);
      Mmouse(710, 335, 2, 2);
      end;
    4:
      begin
      RandomRClick;
      GameTab(tab_Magic);
      Mmouse(710, 335, 2, 2);
      end;
    5:
      begin
        Boredhuman;
        MakeCompass('W');
        GameTab(tab_Magic);
        Mmouse(710, 335, 2, 2);
      end;
    6:
      begin
        Boredhuman;
        MakeCompass('W');
        GameTab(tab_Magic);
        Mmouse(710, 335, 2, 2);
      end;
  end;
end;


Begin
  SMART_FIXSPEED := TRUE;
  SetupSRL;
  DeclarePlayers;
  StartUp;
  Scount := 0;
  GameTab(tab_Magic);
  z := 0;
  Mmouse(710, 335, 2, 2);

  repeat
    if (not LoggedIn) then
      LogInPlayer();

    if (LoggedIn) then
    begin
      AutoAlch;
      Antiban;
    end;
    z := z + 1;

    if (z = 5000) then
      Logout();
      LoginPlayer();
  until (AlchAmt = z)

  Logout();
End.








