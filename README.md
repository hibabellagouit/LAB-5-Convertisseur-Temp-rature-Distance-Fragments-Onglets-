# Convertisseur Température & Distance (Android, Java, Fragments + Onglets)

## Objectif du projet

**Développer une application Android composée de deux onglets :**

 ***Température :*** conversion °C ↔ °F

 ***Distance :*** conversion Km ↔ Miles

**Fonctionnalités supplémentaires :**

 Button Quitter

---

## Dépendances

app/build.gradle
```
dependencies {
    implementation 'com.google.android.material:material:1.12.0'
    implementation 'androidx.viewpager2:viewpager2:1.0.0'
}
```

---

## Interface principale :

**activity_main.xml**

Fichier :
res/layout/activity_main.xml

---

## Classe principale :

**MainActivity.java**

Fichier :
java/com/example/converttabsjava/MainActivity.java 

---

## Adaptateur :

**ViewPagerAdapter.java**

Fichier :
java/com/example/converttabsjava/ViewPagerAdapter.java

---

## Fragment Température

 **Layout :**

    res/layout/fragment_temp.xml

 **Classe Java:**

    TempFragment.java
    
---

## Fragment Distance

 **Layout :**

   res/layout/fragment_distance.xml

 **Classe Java:**

    DistanceFragment.java


---

## Test du projet

**Onglet Température**

Entrer 25 → Résultat : 77°F

**Onglet Distance**

Entrer 10 → Résultat : 6.21 miles

**Touche Retour**

Button du quitte

---

## Vidéo de démonstration

https://github.com/user-attachments/assets/4e47bce0-f9d3-4fea-a453-e43945640d7f

---

## Structure

<img width="247" height="405" alt="image" src="https://github.com/user-attachments/assets/0b1fa526-88d3-4ddc-8678-04dc3e938a45" />











