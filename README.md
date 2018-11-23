# ColorRecHelper
Jerry Dodge's ColorRecord Helper for easy manipulating of Web Colors, Delphi Colors. XE5 Example App, Use-cases, and bad but useful (to me) enhancements.

Some use cases

    - Note: Delphi Hex order is not the same as HTML Hex order
    - examples:
    - HTML Hex Color (Web Development) = #FFFFFF
    - HTML Hex Color Custom Constant (Inside Delphi, if we want to use) = $FFBF00 (Amber,#FFBF00 in web development)
    - Delphi Hex Color = $F0CAA6
    - Delphi TColor = clMoneyGreen
    - R,G,B of a Color (0..255,0..255,0.255)
    - H,S,V of a Color (0..1, 0..1, 0..1 )
    - H(degrees),S,V of a Color (0..360, 0..1, 0..1 )


Natural String to color from editor based input (Goodie Part)


**Trick to make tints of color**
#Convert RGB to HSV and play with Value/Brightness(V field)
#Back convert HSV to RGB.



    procedure TForm1.btnHexDemosViaRecordHelperClick(Sender: TObject);
    var
     col1 : TColorRec;
     myHTMLColor : TNaturalColorHTMLHex;
    begin
        //Delphi to Hex
        col1 := clNone;
        edtHexDelphi.Text := col1.GetDelphiHexWithoutDollar;
        shp2.Brush.Color := col1;
        edtDelphiRGB.Text := IntToStr(col1.FRed) + ', '+IntToStr(col1.FGreen) + ', '+IntToStr(col1.FBlue);

        //Delphi Hex to TColor
        col1.SetDelphiHexWithoutDollarInput(edtHexDelphi.Text);
        shp2.Brush.Color := col1;
        edtDelphiRGB.Text := IntToStr(col1.FRed) + ', '+IntToStr(col1.FGreen) + ', '+IntToStr(col1.FBlue);

        //Delphi Hex to HTML Hex
        col1.SetDelphiHexWithoutDollarInput(edtHexDelphi.Text);
        shp2.Brush.Color := col1;
        edtHexHTML.Text := col1.GetHTMLHexWithoutHash;

        //HTML Hex to TColor
        col1.SetHTMLHexWithoutHashInput(edtHexHTML.Text);
        shp2.Brush.Color := col1;


        col1.SetHTMLHexWithDollar($FFD700);
        myHTMLColor := TNaturalColorHTMLHex.green;
        col1.SetHTMLHexWithDollar(Ord(myHTMLColor));

        col1.SetColorFromNaturalString('orangered');
        shp2.Brush.Color := col1;
    end;

