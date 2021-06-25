### UNIVERSIDADE DE SÃO PAULO, ESCOLA DE ARTES, CIÊNCIAS E HUMANIDADES, PROGRAMA DE PÓS-GRADUAÇÃO EM SISTEMAS DE INFORMAÇÃO
#### Aluno: Renato Banzai - N. USP: 3683321
#### SIN 5014 - Execício Semana 9

1- Implementação de Marching Triangle com média.

```pascal
procedure plotCruveImp;
var  tx,ty,pi,step,x,y,xnext,ynext,e1,e2,e3:real;
var  w,h,xstep,ystep,i,j,fraction:integer;
begin
    h := JPEGExampleForm.Image1.Height;
    w:= JPEGExampleForm.Image1.Width;
    fraction:=10;
    xstep := w div fraction;
    ystep := h div fraction;
    step  := 0.1;
    tx    := -5;
    ty    := 5;

    //looping in each line
    while   (ty > -5) do
    begin
          ynext := ty - step;
          tx    := -5;
          while   (tx < 5) do
          begin
                xnext := tx + step;
                //triangle 1
                e1 := f(tx,ty);
                e2 := f(xnext, ty);
                e3 := f(tx, ynext);

                // plotting lines when edges has different signals

                // e1 inside
                if (e1 < 0) and (e2 > 0) and (e3 > 0) then
                begin
                     JPEGExampleForm.Image1.Canvas.Line(xToInteger(tx),yToInteger((ty+ynext)/2),xToInteger((tx+xnext)/2),yToInteger(ty));
                end;

                // e1 outside
                if (e1 > 0) and (e2 < 0) and (e3 < 0) then
                begin
                     JPEGExampleForm.Image1.Canvas.Line(xToInteger(tx),yToInteger((ty+ynext)/2),xToInteger((tx+xnext)/2),yToInteger(ty));
                end;

                // e2 inside
                if (e1 > 0) and (e2 < 0) and (e3 > 0) then
                begin
                     JPEGExampleForm.Image1.Canvas.Line(xToInteger((tx+xnext)/2),yToInteger(ty),xToInteger((tx+xnext)/2),yToInteger((ty+ynext)/2));
                end;

                // e2 outside
                if (e1 < 0) and (e2 > 0) and (e3 < 0) then
                begin
                     JPEGExampleForm.Image1.Canvas.Line(xToInteger((tx+xnext)/2),yToInteger(ty),xToInteger((tx+xnext)/2),yToInteger((ty+ynext)/2));
                end;

                // e3 inside
                if (e1 > 0) and (e2 > 0) and (e3 < 0) then
                begin
                     JPEGExampleForm.Image1.Canvas.Line(xToInteger(tx),yToInteger((ty+ynext)/2),xToInteger((tx+xnext)/2),yToInteger((ty+ynext)/2));
                end;

                // e3 outside
                if (e1 < 0) and (e2 < 0) and (e3 > 0) then
                begin
                     JPEGExampleForm.Image1.Canvas.Line(xToInteger(tx),yToInteger((ty+ynext)/2),xToInteger((tx+xnext)/2),yToInteger((ty+ynext)/2));
                end;

                // triangle 2
                e1 := f(xnext, ty);
                e2 := f(xnext, ynext);
                e3 := f(tx, ynext);

                // plotting lines when edges has different signals
                // e1 inside
                if (e1 < 0) and (e2 > 0) and (e3 > 0) then
                begin
                     JPEGExampleForm.Image1.Canvas.Line(xToInteger((tx+xnext)/2),yToInteger((ty+ynext)/2),xToInteger(xnext),yToInteger((ty+ynext)/2));
                end;

                // e1 outside
                if (e1 > 0) and (e2 < 0) and (e3 < 0) then
                begin
                     JPEGExampleForm.Image1.Canvas.Line(xToInteger((tx+xnext)/2),yToInteger((ty+ynext)/2),xToInteger(xnext),yToInteger((ty+ynext)/2));
                end;

                // e2 inside
                if (e1 > 0) and (e2 < 0) and (e3 > 0) then
                begin
                     JPEGExampleForm.Image1.Canvas.Line(xToInteger((tx+xnext)/2),yToInteger(ynext),xToInteger(xnext),yToInteger((ty+ynext)/2));
                end;

                // e2 outside
                if (e1 < 0) and (e2 > 0) and (e3 < 0) then
                begin
                     JPEGExampleForm.Image1.Canvas.Line(xToInteger((tx+xnext)/2),yToInteger(ynext),xToInteger(xnext),yToInteger((ty+ynext)/2));
                end;

                // e3 inside
                if (e1 > 0) and (e2 > 0) and (e3 < 0) then
                begin
                     JPEGExampleForm.Image1.Canvas.Line(xToInteger((tx+xnext)/2),yToInteger(ynext),xToInteger((tx+xnext)/2),yToInteger((ty+ynext)/2));
                end;
                // e3 outside
                if (e1 < 0) and (e2 < 0) and (e3 > 0) then
                begin
                     JPEGExampleForm.Image1.Canvas.Line(xToInteger((tx+xnext)/2),yToInteger(ynext),xToInteger((tx+xnext)/2),yToInteger((ty+ynext)/2));
                end;

                tx := xnext;
          end;
          ty := ynext;
    end;
end;
```
