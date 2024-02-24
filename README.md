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

### Mejora

    '''Mejora'''
    import time
    start_time = time.time()
    def collatz(n):
        pasos = 0
        while n != 1:
            if n % 2 == 0:
                n //= 2
            else:
                n = 3 * n + 1
            pasos += 1
        return pasos
    
    n = 16172831301712733
    pasos_totales = collatz(n)
    end_time = time.time()
    print(f"Comenzando en n={n}")
    print(f"La secuencia tiene {pasos_totales} pasos hasta llegar a 1")
    print(f"Tiempo de ejecución: {end_time - start_time:.6f} segundos")

### Saltando bucles

    def collatz(n, memo = {}):
        if n in memo:
            return memo[n]
        pasos = 0
        while n != 1:
            if n % 2 == 0:
                n //= 2
            else:
                n = 3 * n + 1
            pasos += 1
            if n in memo:
                # Se ha detectado un bucle
                return pasos + memo[n] - 1
        memo[n] = pasos
        return pasos

### Uso de operadores bitwise (mejor división)

    def collatz(n, memo = {}):
        if n in memo:
            return memo[n]
        pasos = 0
        while n != 1:
            if n & 1 == 0:
                n >>= 1
            else:
                n = 3 * n + 1
            pasos += 1
            if n in memo:
                # Se ha detectado un bucle
                return pasos + memo[n] - 1
        memo[n] = pasos
        return pasos

### Uso de bibliotecas'''
    from sympy import collatz_conjecture
    
    n = 16172831301712733
    pasos_totales = len(list(collatz_conjecture(n)))
    
    print(f"Comenzando en n={n}")
    print(f"La secuencia tiene {pasos_totales} pasos hasta llegar a 1")
