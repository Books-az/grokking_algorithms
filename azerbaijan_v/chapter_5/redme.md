# Bu fəsildə

*   Siz rekursiya haqqında öyrənirsiniz. Rekursiya bir çox alqoritmdə istifadə olunan kodlaşdırma texnikasıdır. Bu, kitabın sonrakı fəsillərini başa düşmək üçün bir tikinti blokudur.
*   Siz əsas hal və rekursiv halın nə olduğunu öyrənirsiniz. "Böl və hökm et" strategiyası (4-cü fəsil) çətin problemləri həll etmək üçün bu sadə konsepsiyadan istifadə edir.

---

## Original text (English)

# In this chapter

*   You learn about recursion. Recursion is a coding technique used in many algorithms. It's a building block for understanding later chapters in this book.
*   You learn what a base case and a recursive case is. The divide-and-conquer strategy (chapter 4) uses this simple concept to solve hard problems.

# Rekursiya fəsli: Məsləhətlər

Bu fəsildən həyəcanlanıram, çünki o, problemləri həll etməyin zərif bir yolu olan rekursiyanı əhatə edir. Rekursiya mənim sevimli mövzularımdan biridir, lakin o, mübahisəlidir. İnsanlar ya onu sevirlər, ya da nifrət edirlər - və ya bir neçə il sonra sevməyi öyrənənə qədər ondan nifrət edirlər. Şəxsən mən üçüncü kateqoriyada idim.

İşlərinizi asanlaşdırmaq üçün bəzi məsləhətlərim var:

*   Bu fəsildə çoxlu kod nümunələri var. Kodun necə işlədiyini görmək üçün onu özünüz işə salın.
*   Mən rekursiv funksiyalar haqqında danışacağam. Ən azı bir dəfə qələm və kağızla rekursiv funksiyanı addım-addım keçin: "Gəlin görək, mən 5-i faktoriala ötürürəm və sonra beş dəfə 4-ü faktoriala ötürməyi qaytarıram, bu da..." və s. Bu cür funksiyanı keçmək sizə rekursiv funksiyanın necə işlədiyini öyrədəcək.

---

## Original text (English)

# Recursion Chapter: Advice

I'm excited about this chapter because it covers recursion, an elegant way to solve problems. Recursion is one of my favorite topics, but it's divisive. People either love it or hate it—or hate it until they learn to love it a few years later. I personally was in that third camp. To make things easier for you, I have some advice: • This chapter has a lot of code examples. Run the code for yourself to see how it works. • I'll talk about recursive functions. At least once, step through a recursive function with pen and paper: something like, "Let's see, I pass 5 into factorial, and then I return five times passing 4 into factorial, which is . . . ," and so on. Walking through a function like this will teach you how a recursive function works.
# Psevdokod izahı

Bu fəsil həmçinin çoxlu psevdokod ehtiva edir. Psevdokod həll etməyə çalışdığınız problemin kod şəklində yüksək səviyyəli təsviridir. O, kod kimi yazılır, lakin insan nitqinə daha yaxın olmaq üçün nəzərdə tutulub.

---

## Original text (English)

# Pseudocode Explanation

This chapter also includes a lot of pseudocode. Pseudocode is a highlevel description in code of the problem you're trying to solve. It's written like code, but it's meant to be closer to human speech.
# Rekursiya

Tutaq ki, nənənizin çardağını qazırsınız və sirli bir kilidli çamadanla rastlaşırsınız.

---

## Original text (English)

# Recursion

Suppose you're digging through your grandma's attic and come across a mysterious locked suitcase.
![alt text](image.png)

# Rekursiya: Çamadan açarı

Nənə sizə deyir ki, çamadanın açarı çox güman ki, bu digər qutudadır.

---

## Original text (English)

# Recursion: Suitcase Key

Grandma tells you that the key for the suitcase is probably in this other box

![alt text](image-1.png)
# Rekursiya: İç-içə qutular

Bu qutuda daha çox qutular var, həmin qutuların içində də daha çox qutular var. Açar haradasa bir qutudadır. Açarı axtarmaq üçün alqoritminiz nədir? Oxumağa davam etməzdən əvvəl bir alqoritm düşünün.

---

## Original text (English)

# Recursion: Nested Boxes

This box contains more boxes, with more boxes inside those boxes. The key is in a box somewhere. What's your algorithm to search for the key? Think of an algorithm before you read on.
![alt text](image-2.png)

# Rekursiya: İterativ yanaşma

1. Baxılacaq qutuların yığınını düzəldin.
2. Bir qutu götürün və içinə baxın.
3. Əgər qutu tapsanız, onu sonra baxmaq üçün yığına əlavə edin.
4. Əgər açar tapsanız, işiniz bitdi!
5. Təkrarlayın.

Budur alternativ yanaşma:

---

## Original text (English)

# Recursion: Iterative Approach

1. Make a pile of boxes to look through.
2. Grab a box and look through it.
3. If you find a box, add it to the pile to look through later.
4. If you find a key, you're done!
5. Repeat.

Here's an alternate approach:

![alt text](image-3.png)
# Rekursiya: Rekursiv yanaşma

1. Qutunun içinə baxın.
2. Əgər qutu tapsanız, 1-ci addıma keçin.
3. Əgər açar tapsanız, işiniz bitdi!

---

## Original text (English)

# Recursion: Recursive Approach

1. Look through the box.
2. If you find a box, go to step 1.
3. If you find a key, you’re done!

# Rekursiya: While dövrəsi psevdokodu

Hansı yanaşma sizə daha asan görünür? Birinci yanaşma `while` dövrəsindən istifadə edir. Yığın boş olmayana qədər bir qutu götürün və içinə baxın. Budur bəzi psevdokod:

---

## Original text (English)

# Recursion: While Loop Pseudocode

Which approach seems easier to you? The first approach uses a while loop. While the pile isn’t empty, grab a box and look through it. Here’s some pseudocode:

```python
def look_for_key(main_box):
 pile = main_box.make_a_pile_to_look_through()
 while pile is not empty:
 box = pile.grab_a_box()
 for item in box:
 if item.is_a_box():
 pile.append(item)
 elif item.is_a_key():
 print("found the key!")
```

```js
function lookForKey(mainBox) {
  const pile = mainBox.makeAPileToLookThrough();

  while (pile.length > 0) {
    const box = pile.pop();

    for (const item of box) {
      if (item.isABox()) {
        pile.push(item);
      } else if (item.isAKey()) {
        console.log("found the key!");
      }
    }
  }
}

```

# Rekursiya: Funksiya psevdokodu

İkinci yol rekursiyadan istifadə edir. Rekursiya, bir funksiyanın özünü çağırmasıdır. Budur psevdokodda ikinci yol:

---

## Original text (English)

# Recursion: Function Pseudocode

The second way uses recursion. Recursion is where a function calls itself. Here’s the second way in pseudocode:

```py
def look_for_key(box):
 for item in box:
 if item.is_a_box():
 look_for_key(item) Recursion!
 elif item.is_a_key():
 print("found the key!")
```

```js
function lookForKey(box) {
  for (const item of box) {
    if (item.isABox()) {
      lookForKey(item); // Recursion!
    } else if (item.isAKey()) {
      console.log("found the key!");
    }
  }
}
```
# Rekursiya və dövrələr

Hər iki yanaşma eyni şeyi yerinə yetirir, lakin ikinci yanaşma mənə daha aydın görünür. Rekursiya həll yolunu daha aydın etdiyi zaman istifadə olunur. Rekursiyadan istifadə etməyin performans üstünlüyü yoxdur; əslində, dövrələr bəzən performans üçün daha yaxşıdır. Leigh Caldwell-in Stack Overflow-dakı bu sitatını bəyənirəm: "Dövrələr proqramınız üçün performans qazancı əldə edə bilər. Rekursiya proqramçınız üçün performans qazancı əldə edə bilər. Vəziyyətinizdə hansının daha vacib olduğunu seçin!" (http://stackoverflow.com/a/72694/139117). Bir çox vacib alqoritm rekursiyadan istifadə edir, buna görə də bu konsepsiyanı başa düşmək vacibdir.

---

## Original text (English)

# Recursion vs. Loops

Both approaches accomplish the same thing, but the second approach is clearer to me. Recursion is used when it makes the solution clearer. There’s no performance benefit to using recursion; in fact, loops are sometimes better for performance. I like this quote by Leigh Caldwell on Stack Overflow: “Loops may achieve a performance gain for your program. Recursion may achieve a performance gain for your programmer. Choose which is more important in your situation!” (http://stackoverflow.com/a/72694/139117). Many important algorithms use recursion, so it’s important to understand the concept.

# Əsas hal və rekursiv hal

Rekursiv funksiya özünü çağırdığı üçün, sonsuz dövrəyə düşən səhv bir funksiya yazmaq asandır. Məsələn, belə bir geri sayım çap edən bir funksiya yazmaq istədiyinizi fərz edin:

---

## Original text (English)

# Base Case and Recursive Case Intro

Because a recursive function calls itself, it’s easy to write a function incorrectly that ends up in an infinite loop. For example, suppose you want to write a function that prints a countdown like this:
> 3...2...1



You can write it recursively like so:
```py
def countdown(i):
 print(i)
 countdown(i-1)
 countdown(3)
```

```js
function countdown(i) {
  if (i <= 0) return;
  console.log(i);
  countdown(i - 1);
}

countdown(3);
```

# Sonsuz rekursiya problemi

Bu kodu yazın və işə salın. Bir problem görəcəksiniz: bu funksiya sonsuza qədər işləyəcək!

---

## Original text (English)

# Infinite Recursion Problem

Write out this code and run it. You’ll notice a problem: this function will run forever!
![alt text](image-4.png)

> 3...2...1...0...-1...-2...

# Əsas hal və rekursiv halın izahı

(Skriptinizi dayandırmaq üçün Ctrl-C düyməsini basın.) Rekursiv funksiya yazarkən, ona nə vaxt rekursiyanı dayandıracağını bildirməlisiniz. Buna görə də hər rekursiv funksiyanın iki hissəsi var: əsas hal və rekursiv hal. Rekursiv hal funksiyanın özünü çağırdığı haldır. Əsas hal isə funksiyanın özünü yenidən çağırmadığı haldır, beləliklə sonsuz dövrəyə düşmür. Gəlin geri sayım funksiyasına bir əsas hal əlavə edək:

---

## Original text (English)

# Base and Recursive Case Explanation

(Press Ctrl-C to kill your script.) When you write a recursive function, you have to tell it when to stop recursing. That’s why every recursive function has two parts: the base case and the recursive case. The recursive case is when the function calls itself. The base case is when the function doesn’t call itself again, so it doesn’t go into an infinite loop. Let’s add a base case to the countdown function:
```py
def countdown(i):
 if i <= 0: # base case
 print(0)
 return
 else: # recursive case
 print(i)
 countdown(i-1)
```

```js
function countdown(i) {
  if (i <= 0) return; // base case
  console.log(i);
  countdown(i - 1); // recursive case
}

countdown(3);
```
![alt text](image-5.png)

# Yığın (Stack)

Bu bölmə çağırış yığınını (call stack) əhatə edir. Çağırış yığını ümumi proqramlaşdırmada vacib bir konsepsiyadır və rekursiyadan istifadə edərkən də başa düşmək vacibdir.

Tutaq ki, siz barbekü təşkil edirsiniz. Barbekü üçün yapışqan qeydlər yığını şəklində bir tapşırıq siyahısı saxlayırsınız. Massivlər və siyahılar haqqında danışdığımız vaxtı xatırlayırsınız, və sizin bir tapşırıq siyahınız var idi? Siz tapşırıqları siyahıya istənilən yerə əlavə edə və ya təsadüfi elementləri silə bilərdiniz. Yapışqan qeydlər yığını daha sadədir. Bir elementi daxil etdiyiniz zaman, o, siyahının ən üstünə əlavə olunur. Bir elementi oxuduğunuz zaman, yalnız ən üst elementi oxuyursunuz və o, siyahıdan çıxarılır. Beləliklə, tapşırıq siyahınızda yalnız iki əməliyyat var: `push` (daxil etmə) və `pop`.

---

## Original text (English)

# The Stack

This section covers the call stack. The call stack is an important concept in general programming, and it’s also important to understand when using recursion. Suppose you’re throwing a barbecue. You keep a to-do list for the barbecue, in the form of a stack of sticky notes. Remember back when we talked about arrays and lists, and you had a to-do list? You could add to-do items anywhere to the list or delete random items. The stack of sticky notes is much simpler. When you insert an item, it gets added to the top of the list. When you read an item, you only read the topmost item, and it’s taken off the list. So your to-do list has only two actions: push (insert) and pop

![alt text](image-6.png)

# Yığın (Stack) tərifi

Bu məlumat strukturu yığın (stack) adlanır. Yığın sadə bir məlumat strukturudur. Siz bütün bu müddət ərzində fərqinə varmadan bir yığından istifadə etmisiniz!

---

## Original text (English)

# Stack Definition

This data structure is called a stack. You’ve been using a stack this whole time without realizing it!

# Çağırış yığını (Call Stack)

Kompüteriniz daxilən çağırış yığını adlanan bir yığından istifadə edir. Gəlin onu işdə görək. Budur sadə bir funksiya:

---

## Original text (English)

# Call Stack Intro

Your computer uses a stack internally called the call stack. Let’s see it in action. Here’s a simple function:

```py
def greet(name):
 print("hello, " + name + "!")
 greet2(name)
 print("getting ready to say bye...")
 bye()
```

```js
function greet(name) {
  console.log("hello, " + name + "!");
  greet2(name);
  console.log("getting ready to say bye...");
  bye();
}
```

# Çağırış yığını funksiyaları

Bu funksiya sizi salamlayır və sonra iki başqa funksiyanı çağırır. Budur həmin iki funksiya:

---

## Original text (English)

# Call Stack Functions

This function greets you and then calls two other functions. Here are those two functions:




```py
def greet2(name):
 print("how are you, " + name + "?")
def bye():
 print("ok bye! ")
```

```js
function greet2(name) {
  console.log("how are you, " + name + "?");
}

function bye() {
  console.log("ok bye!");
}
```

# Çağırış yığını: Addım-addım izahata giriş

Gəlin bir funksiyanı çağırdığınız zaman nə baş verdiyini addım-addım nəzərdən keçirək.

---

## Original text (English)

# Call Stack Walkthrough Intro

Let’s walk through what happens when you call a function.

# Qeyd

İşləri sadə saxlamaq üçün mən yalnız `greet`, `greet2` və `bye` funksiyalarına edilən çağırışları göstərirəm. `print` funksiyasına edilən çağırışları göstərmirəm.

---

## Original text (English)

# Call Stack Walkthrough Note

To keep things simple, I’m only showing the calls to greet, greet2, and bye. I’m not showing the calls to the print function.

# Çağırış yığını: Addım 1

Tutaq ki, `greet("maggie")` funksiyasını çağırırsınız. Əvvəlcə, kompüteriniz həmin funksiya çağırışı üçün bir yaddaş qutusu ayırır.

---

## Original text (English)

# Call Stack: Step 1

Suppose you call greet("maggie"). First, your computer allocates a box of memory for that function call.

![alt text](image-7.png)





