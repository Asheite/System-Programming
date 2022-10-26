# System Programming
# Ch01

## 什麼是系統程式? 所謂的系統程式就是驅動電腦硬體工作的軟體和韌體(Firmware)就稱為系統程式

## 電腦開機，在尚未載入你的主系統(OS)之前，他有一些必備的工作來驅動電腦的程式就叫做系統程式

## 系統程式的例子: BIOS(基本輸出輸入系統)，今天尚未載入你的OS之前你的BIOS就會先運作(把必要的工作先做近 來)

![](https://i.imgur.com/ZmWk0ql.jpg)


## Utility Program: #include<..>，就是一些System library(公用程式)

## Debugging Aids: 除錯工具、Compilor、core dump

## Assembler: 把組合語言轉成機器碼

## Text editor: 文字編輯器，word、notepad++..

## Bare machine: 裸機，只包含硬體不包含軟體和韌體→不包含系統程式的主機就稱為裸機

## Processor and process management: 簡而言之是處裡CPU(Processor就是我們的CPU、Process是我們的程式。包含我們所寫的或者內建的)

## Device management: USB等等，但能一插即用的原因就是因為有device management

## information management: 存資料這件事就會透過information management，你能夠把資料存進去是因為他能夠幫你把資料存進某個硬碟中，所以你才能取出資料

![](https://i.imgur.com/dyNGFcY.png)


## 我們在寫C時，我們都會寫到#include<>，這東西就是Utility Program and Library。不管在哪裡開發，例如 Linux、mac、windows，系統本身都有一些內建的Library可以使用(開發者所寫的)，我們也可以對系統下指令把一些東西取出來

## 例如DOS: type filename linux: ls -a

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fc4924af-8811-4787-a993-373b49b1bb7b/Untitled.png)

## 3. Marco Processor(巨集處理器): 把長串的東西，用一個簡短的方式給濃縮起來。當我今天程式在執行的時候才把他給展開。在程式執行的時候會做Marco call(Marco Expansion)，呼叫定義的東西

## #define: 用來取代掉部分程式碼

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/67a3830e-390a-4a6b-b3fa-695317116a29/Untitled.png)

## Macro call與function call的差異，Macro call的部份把原本定義的部份去取代原先的部份(不會有把控制權交出去的地方)

## function call的概念與台上講話有點類似，今天你有麥克風你要讓其他人帶你來講化你就要把麥克風(講話的控制權)交出去。把這概念放到程式來看，當你今天main函式執行到一個function時，你會把執行的控制權交出去給這個要執行的function，才能去執行，而要繼續去執行main函式時再把控制權繳回來 。但是相反地，今天你使用的是Marco call的話就不存在把控制權交出去的問題，他只是把定義的東西用你去定義的意義去取代而已，所以在執行時是一路順過去的(一直往下執行)

## 但是我今天Memory是有限的，所以我不能無止境地去使用Marco call，所以才需要用到function call。若今天我夠大的化，我就可以沒有問題遞使用Marco call，在使用marco call的優點就是執行速度比較快(因為不用把控制權交出去)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7cfa8ab9-63e7-494f-a3ed-b247665f2529/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f0ed6f61-971f-4704-afd4-8a933b070635/Untitled.png)

## macro call的部分會佔比較多記憶體，以上面的圖片為例，原本100行的code突然被放大成1090行

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/29a4e633-a153-4b0d-a028-576df11bd3d6/Untitled.png)

## 4.文字編輯器: word、notepad++…

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f4013325-e669-40c4-914e-b9aec2f11f14/Untitled.png)

---

# 1-2 Translator

## 轉譯器的功能: 將原始程式轉換成機器語言

## 我們所寫的code(source code)是給人類看的，而不是給機器看的。機器能看得懂的就只有數字0、1而已。

## 過程來看，編譯器與組譯器的過程會比較相似，因為他們都會經過linker、loader。但是interpreter不一樣(按下Enter就翻譯)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/95f3e217-8170-47f4-aa70-abc9d6e51021/Untitled.png)

## 1.compiler: 寫了一個source program出來，經過compiler會變成一個.obj檔案，再經過linker(把外部變數做連結)產生.com or .exe檔案。最後再經過loader(載入到主記憶體才能執行)來執行程式。

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/52086d48-22c0-4a99-a35e-fe134e11881e/Untitled.png)

## 2.Assembler: 與compiler的差異在於前面的步驟。source code是組合語言以外，他是經過Assembler產生machine code，之後與compiler相同。

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/cac945f0-73a9-4ecb-a21d-00adcdbae2a8/Untitled.png)

## 3.interpreter(解譯器 or 直譯器): 網頁語言(多數)是屬於直譯器。直譯器的概念類似於同步口譯

## 產生中間碼有什麼好處? Ans: debug方便，可以立即知道有沒有錯

## 直譯器的缺點: 執行速度慢，因為要做翻譯。今天我們是compiler or assembler時，我們會產生出執行檔，每次我們要執行時就只要把這個執行檔放進主記憶體裡面就可以執行(不用再經過Linker等等動作)。但是interpreter還是得從原始程式(source program)重新取過來，經過翻譯後再跑出來，所以執行效果比較慢。

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3c0ad0e9-9139-4a99-8f58-9ca8d8eb5a8a/Untitled.png)

## Java: 同時兼具compiler and interpreter

## Java經過java interpreter產生出的Byte code，每次都重新翻譯就可以跑出結果。Java通過java compiler也是會產生出執行檔，所以你以後要執行這個程式時，你只要執行這個執行檔就可以，但是失去跨平台這特性

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bd328d93-1473-4050-99f5-1a88fc3bed15/Untitled.png)

---

# 1-3 linker and loader

## linker: 結合兩個或以上的obj檔案，並且提供一些程式需要的資訊讓他可以做reference

## 我們在寫C的時候會使用的printf、scanf等等，這些函式都不是我們自己寫的蛋是我們可以使用，因為我們把它們include起來了。這邊就是linker把它給連結再一起。所以我們才能用他。

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6b84b553-118c-411d-91cb-96e944e9823f/Untitled.png)

## 今天我們寫一支程式，我們會有一個main函式，假設main函式裡面我們call了一個function叫sub1，那我們就會有sub1這個函式的副程式碼。而在sub1裡面我們又再呼叫了sub2，同理也會有sub2的副程式碼。如果今天這三個函式是獨立成一個一個檔案，再經過compiler之後，我們會得到一 個obj的檔案(main.obj、sub1.obj、sub2.obj)。當我今天編譯過後變成obj檔案時並不代表他們彼此之間就可以呼叫，因為程式main找不到sub1(main裡面沒有sub1)。編譯器會在編譯的過程中去找sub1(因為在main裡面找不到sub1)，所以會去使用external reference(外部變數)把sub1視為是一個外部變數，所以在翻譯成機器碼的時候就會先call一個暫時的記憶體位置(原因: 不知道在哪裡)，sub1 call sub2也是同樣道理。所以當程式內的函數彼此要呼叫的後就需要透過linker把他們做連結

## 在右邊的部分，是我們透過linker把程式變成一個可執行的模組。而做邊原先我們因為不知道函式位置所以呼叫一個暫時的位置這件事，會因為Linker而解決，我們就可以找到實際上這些副程式的位置。

## 所以我們會說Linker在做的事是在做**重定位**

## 右邊我們的main函式的起始位置是1000，但是並不是每次她的位置都是在1000，只是因為主記憶體判斷說這邊1000剛好有空位，但是下一次並不一定會在這個位置。假設我們今天main的起始位置是在3000，而sub1的位置應該會是在307A、sub2的起始位置在3120，這個就叫做重定位。

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3f5f997e-a17a-429d-8569-851bb8831eba/Untitled.png)

## loader(載入器): 將執行模組載入到主記憶體裡面來執行。

## a. Allocation: 我們要決定把程式放到哪一個位置。我們要執行程式並不是一半下執行就可以開始執行，事實上會先分配一個我的程式可以容納的空間，我才可以執行(先幫我找到一個適合的大小，剛好我的程式可以放得進來)。執行模組該放在哪個位置就是靠loader

## b. Linking: 將外部變數做連結。當某個涵是使用到的變數或是參考到的變數、函式不在目前的函示裡頭，而是被定義在其他地方時，就會透過連結器把它連結在一起。

## c. relocation: 重定位。

## d. loading: 把執行模組載入到主記憶體裡頭。

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e0ac3d6f-c220-4fbd-a059-e897f2ed8122/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/95906ef4-0542-4b8a-ae29-c8ade20c52ab/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a585a9c6-b15e-4c87-abca-4b02b23d4640/Untitled.png)

---

# 1.4  Operating System

## 裸機必須加上系統程式才能工作。嚴格來說裸機需要加入作業系統才可以進行操作、管理等等。

## processor(CPU): 程式在執行當中，作業系統會把我們要執行的程式視為一個處理元(process)。大部分電腦的CPU都是在處理process。先後順序也是由我們的處理元來管理

 

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3ef30320-1018-4ad2-95e0-76ad3c59e564/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4c890fd5-ee8c-4557-8ae8-c21f72624266/Untitled.png)

---

# 1.5 Relation between system software and machine architecture(設計組譯器)

## 什麼是跟機器有關? 例如: 指令集(instruction set)、指令的格式(instruction format)、定址模式(Addressing mode)…

## 跟機器無關的: 我們設己的邏輯、策略、two passes assembler

## 今天我們針對80x86的架構去進行設計，我們要透過assembler去把我們的組合語言翻譯成machine code，我們就需要透過與x86相關的東西才可以去翻譯。除了要了解他的指令集還要去了解它有哪些指令，並且要知道有沒有他的指令格式。那當我們執行指令可能會取一些東西出來，而這些東西放的位置會放在哪就跟addressing mode有關。

## two passes assembler(x86 or SIC都要): 我們寫一個組義氣，需要透過兩次性的處理。第一次，我們先看我們組合語言傳過來的有那些指令，把每個指令儲存到相對應的table裡面。第二次，進行定位，把我們原先找到或沒找到的都要做定位，找到相對應的位置。

## 與機器有關的意思是指說當我今天設計的不是x86的話，那我設計的方式就會不同，而與機器有關就代表這些東西不會因為架構(機器)的改變而改變

## 與機器相關是具有時代的任務，過去的東西可能在現在無法使用

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7198fd4d-2789-4eb1-a5fe-2841f11e621f/Untitled.png)

---

# 1.6 SIC(simplified Instructional Computer SIC or SIC/XE ) Machine Structure

## SIC本身是一個虛擬的機器

## A(Accumlator累加器): 做相加的時候會做累加(在x86時事較AX)

## X(index register索引暫存器)

## L(Linkage register):

## B(Base register): 要進行重定位時都會用到(x86: segment register)

## S(General Working Register):

## T(General Working register):

## F(Floating Point Accumulator): 浮點數累加器

## PC(Program Counter): 不管是現在、過去、未來的機器都會有PC的存在，主要是用來指向線在執行指令的下一個指令的位置(Location counter or Instruction Counter or Instruction Pointer)

## SW(Status Word):

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4d8ae81d-06e3-4975-a685-84dc5cf05fdf/Untitled.png)

## SIC Instruction set

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1ebdedb6-0516-4c27-a3a6-6cb7bf3149b9/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9546dbb3-33c5-4f32-860a-02d0e1364c19/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/580b2bdd-25a3-406b-92fc-ad4886f89b48/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c8e371c6-ca9c-4cd5-8396-8b3f4d98c900/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3a2dfb68-3fd3-49e9-acfa-573e8ab2e15f/Untitled.png)

## SIC的指令週期

## 指令週期的意思: 執行一個指令所需要的相關動作或步驟

## 指令週期可以分為兩種找尋週期(Fetch cycle)和執行週期(execute cycle)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c8ac3432-9a6c-4f57-88df-906cfc5fb2b7/Untitled.png)

## 執行週期又可以再分成四個小周期

## B. 若我們有要運算的話，我會去記憶體取找尋這個變數在哪裡並找出他的值

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/021dff84-6520-48f0-81b2-bd612c04c80e/Untitled.png)

## 以ADD DATA(累加)為例:

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/897a813f-627a-43ca-a8ca-d714160c8167/Untitled.png)

## 一開始我們會從PC(Program Counter)去找指令。

## 假設我們指令是在第三行裡面，我們就去抓第三行。這時候就進入了Fetch cycle，他會把第三行的指令的位置放在MAR(Memory Address Register)裡面。

## 做到這邊我就要去要求主記憶體把它裡面的內容給拿出來，因為現在我只知道第三行這個位置是在03060015，但是我不知道他是甚麼指令，因此我就會要求Memory回傳給我這0306這個裡面放甚麼。

## 再之後，當我們把它拿出來之後，我們再將03060015這個東西放到MBR(Memory Buffer Register)裡面(仍在Fetch cycle)。

## 到目前為止我們只是把這個指令抓起來並存放在MBR裡面，但是我們還是不知道這個指令要我們做些甚麼，所以我們會把這個指令放到IR(Instruction Register)裡面，透過Decoder去解碼。到這邊我們才知道這個指令要做甚麼，以ADD DAT為例，也就是說我們現在才知道這個指令是要做累加。

## 下一個步驟就是要去找DATA是甚麼，因為我們知道他現在這個指令要做累加了，所以我們還要知道要把甚麼值加到AX裡面。所以我們會到DATA相對應的位置裡面去找他的值。假設DATA放在0015裡面，那我們就把DATA放到MAR裡面來。這時候就近到Fetch operand cycle這個步驟了。接下來，我們會把0015這指令丟到Memory裡面，也就是說要記憶體把0015裡面存放的值還給我。假設我們這個0015的值是100好了，我們會把100放到MBR裡面才能進到運算的cycle

## 進到計算周期時就不會是再MBR進行，而是會到邏輯運算單元去執行。以100為例，這邊就是100進到ALU去計算、執行

## 最後把計算/執行結果儲存起來

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/996ff795-441b-4aa1-a77e-2dc0cfd9f05e/Untitled.png)

## SIC機器結構 Addressing(定址)

## 不只是在SIC，在x86也是有的

## a.立即定指法(Immediate addressing): 機器會看你後面的數值是多少並把它放到相對應的位置。以LDA #40為例，機器會先找出LDA他的機器碼，在看後面的數值並放上去就好，也就是說40也會出現在機器碼裡面→0040(LDA: 00)。在x86裡面，以MOV AL, 40H為例，MOV會把後面的數值放到前面來，在x86裡面也是會直接去找MOV這個指令的機器碼，在翻譯機器碼的過程中40也會出現在我們的機器碼。

## b.直接定址法(Direct Addressing / Simple Addressing): 以LDA DATA為例，我們要查找LDA這個指令以外還要去查找DATA的值是甚麼。在這裡我們並不是直接找DATA相關的機器碼，而是要先去找DATA的位置的值是多少，再將這個位置放到機器碼裡面，假設今天DATA的位置是在1500，我們會得到 001500

## c.間接定址法(Indirect Addressing): 會在前面放上@符號，以J @RETADR為例，假設今天RETDAR的位置是1500，他並不會直接把1500放在機器碼上，而是取得1500裡面的值

## 索引定址法(index or Relative Addressing): 以LDCH DATA, X為例，當今天你看到這個X，就可以知道這個是一個索引的方式來定址。假設今天DATA的位置是1500，他並不是把1500放到機器碼裡面，他還會加上索引(X)，這樣才是我們想要翻譯的對象。常常被用來當成陣列內的存取元素來使用。在x86會用 MOV Ax, DATA[SI]，SI相當於X

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/29c7b3e1-7f96-4240-a0b5-5a9426498892/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5c37e896-558c-4f72-99c7-2e755065805e/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7e9c5c6b-6db7-422d-8c05-6cad65bfc9f5/Untitled.png)

## Instruction Type:

## SIC我們又分成SIC和SIC/XE，而SIC的Type的部分就只有一種Standard Type(標準模式)。但是SIC/XE有4種模式

## a. standard type: 若今天x=0，則我們是做直接定址。而今天x=1的話就是把x當作index register(索引值)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d5ba5ce2-25c1-4c40-89a2-5030aeac8dff/Untitled.png)

## 我該如何知道我的SIC指令是SIC的哪一種模式? 底下圖裡Format 3/4就是說它可以同時作為指令3或是指令4(看他當時的指令的格式來決定3 or 4)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e36d8677-8ce3-43e6-a333-2acc9acbba09/Untitled.png)

## a. Format 1: 就1個指令的名稱，所以我們最後回答C4就可以了

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d1fb2b3b-774c-4fe3-aea0-f2ee872e3117/Untitled.png)

## b. Format 2: 前面就是Opcode再來是r1, r2。以COMPR r1, r2為例，他的寫法就是A0 r1, r2

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e4bd8122-ee8a-4ff5-85ae-63cd026a7751/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8a97738e-0eb6-4fc3-af29-4c30747087bd/Untitled.png)

## Format 3、Format 4是絕大部分SIC指令裡面會用到的模式

## Format 3: 後面所接的disp是距離(計算距離)

## Format 4:後面街的是位置

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/97b55dca-7357-4eb5-88d3-6aff54d6774e/Untitled.png)

## 區別Format 3 and 4

## 先從e開始去判斷，今天0代表的是Format 3，1代表的是Format 4。以"+"去做區別，假設今天的指令是+JSB，前面有個+代表他是format 4，若前面是空的就是format 3

## b(base register)、p(program counter)、x(index register): 用來看重定位來判斷，今天用哪一個就是設定為1。而base register and program counter都是作為program relocation的使用，若指令裡有x的話就代表是使用index register

## i: 用來判斷是不是在使用immediate mode，使用立即定址法的方式，只需要看有沒有"#"就可以知道是不是使用立即定址法

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5e131044-938c-48ca-86cc-db0e5819a78b/Untitled.png)

## 今天你把i設為1(n為0)，代表使用的是立即定址法(前面是"@”)。若把n設為1(i為0)代表使用的是間接定址法(前面會有"@”)

## 若今天你i and n都設為0時，代表你使用的是直接定址法(direct addressing)，同時也代表是一個標準模式。相反地都設為1的時候代表示一個XE的type。所以如何判斷SIC or SIC/XE呢? 就利用i、n兩個值去判斷

## base register and program counter的部分是被使用在重定位，所以說當今天把b設為1、p設為0，我們使用就是base register來進行重定位。若b=0, p=1代表是使用program counter來進行重定位。若兩個(b and p)當設置為0的話，你的target address就直接是disp或者是address

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ae69339d-c474-444d-9b99-f267c6a0e635/Untitled.png)

## 索引定址的地方(indexing addressing):

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ea371318-f0fe-42de-b335-76519ee674eb/Untitled.png)

## 相對位置的索引定址: 使用BASE REGISTER OR PROGRAM COUNTER來進行城市位置的定址

## 底下第30行 AA DB是我們要找的地方，而當我們要找AA時，上面的STA AA實際上就會變成STA 30。這是我們程式碼第一次經過compiler and assembler他會這樣子去做。以下只是一種例子而已，剛好是從0開始去擺。但是實際上擺放在指令的位置不一定每次都是從0開始，也會有可能從其他地方開使擺放。

## 假設我們今天是從1500開始去擺放，那我們AA DB的位置應該會在1530。我們要去讀取AA就要去30行的位置，可是在這例子中是讀取不到的，因為AA的位置是在1530。loader會幫我們進行重定位來去把30改1530，以找到AA，但是這樣是不聰明的做法。所以實際上，我們會把起始的儲存位置放在Base register or Program counter，所以當我們在找AA時，他會把這個起始位置去加上30(原先我們知道的地方)來找到

## 現在位置 = 起始位置 + 定義的相對位置

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/da8a85bb-4e0e-47eb-b275-9ad3937392fb/Untitled.png)

## 

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8bb86aaf-a563-467c-b763-a81173aeea32/Untitled.png)

## 未來不管你是使用哪個作業系統是是機器你都要能夠知道哪些是executable instruction，還要可以判斷哪些是pseudo instruction。

## Executable instruction: 會翻譯成機器碼

## Pseudo instruction: 不會翻譯成機器碼

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/977f8ffc-86b4-41c9-a304-303e785f34fa/Untitled.png)

## 左邊是SIC 右邊是SIC/XE

## 上半部是屬於executable instruction，而下半部是Pseudo instruction

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e76e19a3-d596-4413-a7a9-0cd8050139ae/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/02697ced-6130-412f-852b-bee3f8994471/Untitled.png)

---

# 1.7 80XX Assembly Language!

![](https://i.imgur.com/tCSTweV.png)
