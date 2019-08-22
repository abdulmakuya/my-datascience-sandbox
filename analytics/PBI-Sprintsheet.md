```dax
v12 = SWITCH (
    ((Data[v6] = "TOP")),
    //Vodacom starting with 255 and 0
    ( (LEFT(Data[v7],5) = "25574") || (LEFT(Data[v7],5) = "25575") || (LEFT(Data[v7],5) = "25576") ), "VODACOM",
    ( (LEFT(Data[v7],2) = "74") || (LEFT(Data[v7],2) = "75") ) , "VODACOM",

    //Airtel starting with 255 and 0
    ( (LEFT(Data[v7],5) = "25568") || (LEFT(Data[v7],5) = "25569") || (LEFT(Data[v7],5) = "25578") ), "AIRTEL",
    ( (LEFT(Data[v7],2) = "68") || (LEFT(Data[v7],2) = "69") || (LEFT(Data[v7],2) = "78") ) , "AIRTEL",

    //Zantel starting with 255 and 0
    ( (LEFT(Data[v7],5) = "25577") ), "ZANTEL",
    ( (LEFT(Data[v7],3) = "077") ) , "ZANTEL",

    //Smile starting with 255 and 0
    ( (LEFT(Data[v7],5) = "25566") ), "SMILE",
    ( (LEFT(Data[v7],3) = "066") ) , "SMILE",


    "NOT YET CATEGORIZED"
)

```
