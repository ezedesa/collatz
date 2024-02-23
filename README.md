# Collatz conjeture
### A little try

    import time
    start_time = time.time()
    n=16172831301712733
    while n>1:
        print("Comenzando en n=", n)
        pasos=0
        while n>1:
            while n % 2==0:
                n=n // 2
                pasos=pasos+1
            while n % 2 !=0 and n !=1:
                 n=n*3+1
                 pasos=pasos+1
        end_time = time.time()
        print("la secuencia tiene", pasos, "pasos hasta llegar a 1")
        print(f"Tiempo de ejecución: {end_time - start_time:.6f} segundos")
    
    
    
    '''Resultado:
    Comenzando en n= 16172831301712733
     la secuencia tiene1300 pasos hasta llegar a  1'''
