"""
Simple Check of prime numbers, with the empiric indian math method.
"""


import math
import pickle

def _test(number):
	if type(number) == int:
		if number >= 1:
			return True
	raise ValueError("The argument is not integer or integer positive.")


"""
This function requires a integer number and 
return True if is prime or False if not
"""
def isPrime(number):
	if(_test(number)):
		global firstDivisor
		limit = range(2,int(math.sqrt(number))+1)
		for eachDivisor in limit:
			if number % eachDivisor == 0:
				firstDivisor = eachDivisor
				return False
		return True

def isPrimeSmart(number):
	if(_test(number)):
		global firstDivisor
		limit = range(2,int(math.sqrt(number))+1)
		primos = _loadPrime()
		for eachDivisor in primos:
			if eachDivisor >= limit:
				break
			if number % eachDivisor == 0:
				firstDivisor = eachDivisor
				return False
		return True

"""
This function requires a integer number and return
a list of prime components of this number
"""
def primeComponents(number):
	if(_test(number)):
		pComponents = set([1])
		while(True):
			if(isPrime(number) == False):
				pComponents.add(firstDivisor)
				number = number // firstDivisor
			else:
				pComponents.add(number)
				return sorted(list(pComponents))

def primeRange(number,initial=2):
	if(_test(number)):
		pr = set([1])
		for eachNumber in range(initial,number):
			if(isPrime(eachNumber)):
				pr.add(eachNumber)
		lista = sorted(list(pr))
		_dumpPrime(lista)
		return lista

def primeRangeSmart(number):
	if(_test(number)):
		lista = _loadPrime()
		if(len(lista) != 0):
			if(lista[-1] >= number):
				return [eachNumber for eachNumber in lista if eachNumber < number]
			else:
				list(set(lista).union(set(primeRange(number,lista[-1]))))
		return primeRange(number)

def _loadPrime():
	try:
		with open('prime.dat','rb') as arquivo:
			return pickle.load(arquivo)
	except:
		return list()

def _dumpPrime(lista):
	total = set(_loadPrime()).union(set(lista))
	try:
		with open('prime.dat','wb') as arquivo:
			pickle.dump(list(total),arquivo)
			return True
	except:
		return False





