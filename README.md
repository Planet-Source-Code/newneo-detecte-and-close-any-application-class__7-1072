<div align="center">

## Detecte and close any application class


</div>

### Description

This code read all running process on the system, and detect classname called 'Notepad' (Do you know what is this? :P) Then, it gets the Handle, and post a message for close the app.
 
### More Info
 
Well, you need a Timer (called Timer1) and 2 labels (called Label1 and Label2).

And you must declare on "uses" "ShellApi" !


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[NeWNeO](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/newneo.md)
**Level**          |Intermediate
**User Rating**    |4.5 (18 globes from 4 users)
**Compatibility**  |Delphi 7, Delphi 6, Delphi 5
**Category**       |[Windows API Call/ Explanation](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/windows-api-call-explanation__7-39.md)
**World**          |[Delphi](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/delphi.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/newneo-detecte-and-close-any-application-class__7-1072/archive/master.zip)





### Source Code

```
Function TotalAPP(HWND : Thandle; Param : Integer): BOOL; stdcall;
var
Buff, NameOfClass : array[0..255] of char;
wintext,handle,parent,clase: string;
AppHandle: cardinal;
intExitCode: integer;
begin
  GetWindowText(HWND,PChar(LongInt(@Buff)),255);
  GetClassName(HWND,Pchar(LongInt(@NameOfClass)),255);
  WinText:=buff;
  Handle:=IntToStr(LongInt(HWND));
  Parent:=IntToStr(LongInt(GetParent(hwnd)));
  Clase:=NameOfClass;
  if clase = 'Notepad'
   then begin
   form1.label1.caption := (Wintext+' '+Handle+' '+parent+' '+nameofclass);
   Apphandle := integer(handle);
   form1.label2.caption := (handle);
   GetExitCodeprocess(AppHandle,cardinal(intExitCode));
   Postmessage(integer(Apphandle), WM_DESTROY, intExitCode, 0);
   end;
  end;
procedure TForm1.Timer1Timer(Sender: TObject);
begin
Enumwindows(@TotalAPP,0);
end;
```

