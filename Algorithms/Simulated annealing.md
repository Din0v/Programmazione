# Simulated annealing

Is an algoithm which is used to find an optimal local maxima, inspired by the annealing of metals. 

```Java
public string StartAnnealing()
{
    TspDataReader.computeData();
    ArrayList list = new ArrayList();
    //primary configuration of cities
    int [] current={0,1,2,3,4,5,6,7,8,9,10,11,12,13,14};
    //the next configuration of cities to be tested
    int []next=new int[15];
    int iteration =-1;
    //the probability
    double proba;
    double alpha =0.999;
    double temperature = 400.0;
    double epsilon = 0.001;
    double delta;
    double distance = TspDataReader.computeDistance(current);

    //while the temperature did not reach epsilon
    while(temperature > epsilon)
    {
        iteration++;
    
        //get the next random permutation of distances 
        computeNext(current,next);
        //compute the distance of the new permuted configuration
        delta = TspDataReader.computeDistance(next)-distance;
        //if the new distance is better accept it and assign it
        if(delta<0)
        {
            assign(current,next);
            distance = delta+distance;
        }
        else
        {
            proba = rnd.Next();
            //if the new distance is worse accept 
            //it but with a probability level
            //if the probability is less than 
            //E to the power -delta/temperature.
            //otherwise the old value is kept
            if(proba< Math.Exp(-delta/temperature))
            {
                assign(current,next);
                distance = delta+distance;
            }
        }
        //cooling process on every iteration
        temperature *=alpha;
        //print every 400 iterations
        if (iteration%400==0)
        Console.WriteLine(distance);
    }
    try
    {
        return "best distance is"+distance;
    }
    catch
    {
        return "error";
    }
}

/// <summary>
/// compute a new next configuration
/// and save the old next as current
/// </summary>
/// <param name="c">current configuration</param>
/// <param name="n">next configuration</param>
void computeNext(int[] c, int[] n)
{
    for(int i=0;i<c.Length;i++)
    n[i]=c[i];
    int i1 = (int)(rnd.Next(14))+1;
    int i2 = (int)(rnd.Next(14))+1;
    int aux = n[i1];
    n[i1]=n[i2];
    n[i2]=aux;
}
```

Simulated Annealing è un algoritmo di ottimizzazione basato sull'annealing simulato, un processo di raffreddamento graduale utilizzato in metallurgia per rendere i materiali più resistenti.

L'idea alla base dell'algoritmo di simulated annealing è quella di trovare il minimo (o massimo) di una funzione a più dimensioni, spostandosi da un punto di partenza alla soluzione finale attraverso una serie di passi che vanno "a scendere di temperatura", cioè a diventare sempre meno probabili man mano che ci si avvicina alla soluzione finale.

In pratica, l'algoritmo di simulated annealing inizia con una temperatura iniziale elevata e con un punto di partenza nello spazio delle soluzioni. A ogni passo, viene generato un nuovo punto vicino al punto attuale e viene calcolata la differenza di energia (cioè la differenza di valore della funzione) tra il nuovo punto e il punto attuale. Se la differenza è negativa, il nuovo punto viene accettato come nuovo punto attuale. Se invece la differenza è positiva, il nuovo punto viene accettato con una probabilità che dipende dalla temperatura corrente e dalla differenza di energia.

L'algoritmo continua a ripetere questi passi, abbassando gradualmente la temperatura ad ogni iterazione, fino a raggiungere una temperatura finale molto bassa. A questo punto, l'algoritmo si ferma e restituisce il punto attuale come soluzione ottimale.

Spero di aver chiarito in modo soddisfacente cos'è l'algoritmo di simulated annealing. Se hai altre domande o vuoi saperne di più, non esitare a chiedere!

### Tags 
#Algorithms 