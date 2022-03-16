# DAX
# How to create slicer with multiple columns
# There are five addidtional columns in the Data Table, Each column contains its own identical value.
# Now you need to merge the 5 columns into one and add it to the slicer
![grafik](https://user-images.githubusercontent.com/84840321/158632456-394a009c-faa4-41ea-8753-3aa90d810b18.png)

# The following DAX was created.
# 1. Merge five columns into one
AllMonate = 
COMBINEVALUES (
    ";",
    'DateTable'[1 Monat],
    'DateTable'[12 Monate],
    'DateTable'[3 Monate],
    'DateTable'[6 Monate],
    'DateTable'[9 Monate]
)
# 2. create a new table "Allone"
ALLone = 
DISTINCT (
    UNION (
        SELECTCOLUMNS (
            'DateTable',
            "Zeitregeln", 'DateTable'[1 Monat],
            "AllMonate", 'DateTable'[AllMonate]
        ),
        SELECTCOLUMNS (
            'DateTable',
            "Zeitregeln", 'DateTable'[12 Monate],
            "AllMonate", 'DateTable'[AllMonate]
        ),
        SELECTCOLUMNS (
            'DateTable',
            "Zeitregeln", 'DateTable'[3 Monate],
            "AllMonate", 'DateTable'[AllMonate]
        ),
        SELECTCOLUMNS (
            'DateTable',
            "Zeitregeln", 'DateTable'[6 Monate],
            "AllMonate", 'DateTable'[AllMonate]
        ),
        SELECTCOLUMNS (
            'DateTable',
            "Zeitregeln", 'DateTable'[9 Monate],
            "AllMonate", 'DateTable'[AllMonate]
        )
    )
)

![grafik](https://user-images.githubusercontent.com/84840321/158634052-85c04813-a67d-4beb-944f-88ea2c5ab9de.png)


# 3. Create many-to-many relationships with DataTable
![grafik](https://user-images.githubusercontent.com/84840321/158633911-ec927398-ce72-4de2-92b2-53244753e21f.png)



