1. Structure de l'Interface (activity_main.xml)L'interface principale contient le TabLayout pour la navigation et le ViewPager2 pour afficher les fragments.XML<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical">

    <com.google.android.material.tabs.TabLayout
        android:id="@+id/tabLayout"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:background="?attr/colorPrimary"
        app:tabTextColor="#FFFFFF"
        app:tabSelectedTextColor="#FFEB3B" />

    <androidx.viewpager2.widget.ViewPager2
        android:id="@+id/viewPager"
        android:layout_width="match_parent"
        android:layout_height="0dp"
        android:layout_weight="1" />

    <Button
        android:id="@+id/btnQuit"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Quitter l'application"
        android:layout_margin="16dp" />

</LinearLayout>
2. Logique de Navigation (MainActivity.java)Cette classe gère la liaison entre les onglets et le contenu.Javapublic class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        TabLayout tabLayout = findViewById(R.id.tabLayout);
        ViewPager2 viewPager = findViewById(R.id.viewPager);
        Button btnQuit = findViewById(R.id.btnQuit);

        viewPager.setAdapter(new ViewPagerAdapter(this));

        new TabLayoutMediator(tabLayout, viewPager, (tab, position) -> {
            tab.setText(position == 0 ? "Température" : "Distance");
        }).attach();

        btnQuit.setOnClickListener(v -> finish());
    }
}
3. Adaptateur des Fragments (ViewPagerAdapter.java)Il définit quel fragment afficher selon l'onglet sélectionné.Javapublic class ViewPagerAdapter extends FragmentStateAdapter {
    public ViewPagerAdapter(@NonNull FragmentActivity fragmentActivity) {
        super(fragmentActivity);
    }

    @NonNull
    @Override
    public Fragment createFragment(int position) {
        return (position == 0) ? new TempFragment() : new DistanceFragment();
    }

    @Override
    public int getItemCount() { return 2; }
}
4. Modules de Conversion (Fragments)Chaque fragment suit la même logique : un champ de saisie (EditText), un bouton (Button) et un affichage (TextView).A. Fragment Température (25°C → 77°F)Formule utilisée : $F = (C \times 9/5) + 32$Code Java simplifié (TempFragment.java) :JavabtnConvert.setOnClickListener(v -> {
    double celsius = Double.parseDouble(editInput.getText().toString());
    double fahr = (celsius * 9/5) + 32;
    txtResult.setText(String.format("%.2f °F", fahr));
});
B. Fragment Distance (10 Km → 6.21 Miles)Formule utilisée : $Miles = Km \times 0.621371$Code Java simplifié (DistanceFragment.java) :JavabtnConvert.setOnClickListener(v -> {
    double km = Double.parseDouble(editInput.getText().toString());
    double miles = km * 0.621371;
    txtResult.setText(String.format("%.2f miles", miles));
});
5. Résumé des TestsType de conversionEntréeFormuleRésultat AttenduTempérature25$x \times 1.8 + 32$77.00 °FDistance10$x \times 0.621$6.21 miles

---

## Vidéo de démonstration

https://github.com/user-attachments/assets/4e47bce0-f9d3-4fea-a453-e43945640d7f














