# Salario
#include <iostream>
#include <string>
#include <sstream>
#include <stdio.h>
#include <ctype.h>
using namespace std;
class Coleccion{
private:
	float salario[250];
	int tamanno;
	int cantidad;
	
public:
	Coleccion(){
		tamanno = 10;
		cantidad = 10;
		for (int i = 0; i < tamanno; i++){
			salario[0] = 5000;
			salario[1] = 100000;
			salario[2] = 8500;
			salario[3] = 1300;
			salario[4] = 7400;
			salario[5] = 22200;
			salario[6] = 60000;
			salario[7] = 32000;
			salario[8] = 44900;
			salario[9] = 9300;
			
		}
	}
	
	string toString(){
		stringstream ss;
		ss<<"-------------------NUMEROS-----------------------"<<endl<<endl;
		for (int i = 0; i < cantidad; i++){
			
			ss <<" La posicion " << i << " es: " << salario[i] << endl;
		}
		return ss.str();
	}
	~Coleccion(){
		
	}
	void setCantidad(int cantidad){
		this->cantidad=cantidad;
	}
	int getCantidad(){
		return this->cantidad;
	}
	float montoAjusSalMin(float salMin){
		float  resta=0, suma=0;
		for (int i = 0; i < cantidad; i++){
			if(salario[i] < salMin){
				resta=salMin-salario[i];
				suma+=resta;
			}
			else{
				suma+=0;
			}

		}
		return suma;
	}
	void ajusteSalMin(float salMin){
		for (int i = 0; i < cantidad; i++){
			if(salario[i] < salMin){
				salario[i]=salMin;
				
			}
			
		}
	}
	float calculoCotizacion(){
		float  multiplicacion=0, suma=0,resta=0;
		for (int i = 0; i < cantidad; i++){
				multiplicacion=salario[i]*0.917;
				resta=salario[i]-multiplicacion;
				suma+=resta;			
		}
		return suma;
	}
};
int main(int argc, char *argv[]) {
	Coleccion a;
	float min=0,capital=0;
	cout<<a.toString()<<endl;
	
	cout<<"Ingrese el minimo de salario"<<endl;
	cin>>min;
	cout<<"Ingrese el capital de la empresa"<<endl;
	cin>>capital;
	cout<<a.montoAjusSalMin(min)<<endl;
	a.ajusteSalMin(min);
	cout<<a.toString()<<endl;
	cout<<"La cotizacion es: "<<a.calculoCotizacion()<<endl;
	cout<<"Tendra un balance positivo?: "<<a.deterSituaFinanciera(capital,min)<<endl;
	return 0;
}
