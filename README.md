# guess-the-door
# 🧠 Qapını Tap! (guess-the-door)

Bu oyun məşhur guess-the-door paradoksuna əsaslanır. Oyunda 3 qapıdan birində hədiyyə gizlənib. Sən əvvəlcə birini seçirsən, sonra bir səhv qapı açılır. Sonda dəyişmək istəyib-istəmədiyin soruşulur.

## 🎮 Necə oynanılır?

- 3 qapı var: 1, 2, 3
- Birini seçirsən
- Kompüter bir boş qapını açır
- Dəyişmək istəyirsənsə daha çox şansın olur!
-------------------------------------------

Kod hissəsi:

import random

score = 0

while True:
    gift_door = random.randint(1, 3)
    print("\n🟥 🟥 🟥")
    print("Qarşında 3 qapı var: 1, 2, 3")
    
    choice = int(input("Bir qapı seç (1, 2 və ya 3): "))
    
    doors = [1, 2, 3]
    doors.remove(choice)
    if gift_door in doors:
        doors.remove(gift_door)
    opened = random.choice(doors)
    print(f"Qapı {opened} açıldı — orası boşdur.")
    
    change = input("Qapını dəyişmək istəyirsən? (bəli/xeyr): ").lower()
    if change == "bəli":
        new_choices = [1, 2, 3]
        new_choices.remove(choice)
        new_choices.remove(opened)
        choice = new_choices[0]
 
    if choice == gift_door:
        print("🎉 Təbriklər! Hədiyyəni tapdın!")
        score += 1
    else:
        print("❌ Təəssüf! Səhv qapı.")

    print(f"Toplam xal: {score}")
    
    again = input("Yenidən oynamaq istəyirsən? (bəli/xeyr): ").lower()
    if again != "bəli":
        break
