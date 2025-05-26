# EQBSCQ: Experimental Quantum Battle of the Sexes: Classical &amp; Quantum

Un repositorio para implementar y comparar la versión clásica y cuántica del juego **Battle of the Sexes** bajo el esquema Eisert–Wilkens–Lewenstein (EWL), empleando Qiskit para simulación local (Aer) y ejecución en hardware real de IBM Quantum.

---

## 📋 Contenido

- [Descripción del Proyecto](#descripción-del-proyecto)  
- [Requisitos](#requisitos)  
- [Instalación](#instalación)  
- [Estructura de Código](#estructura-de-código)  
- [Uso](#uso)  
  - [Simulación Local](#simulación-local)  
  - [Ejecución en Hardware](#ejecución-en-hardware)  
  - [Barrido de Parámetros](#barrido-de-parámetros)  
- [Metodología](#metodología)  
- [Resultados y Visualización](#resultados-y-visualización)  
- [Contribuciones](#contribuciones)  
- [Licencia](#licencia)  

---

## Descripción del Proyecto

El objetivo de **QBS-CQS** es validar experimentalmente el juego *Battle of the Sexes*:

1. **Clásico**: Cálculo de pagos en equilibrio mixto como referencia.  
2. **Cuántico**: Implementación EWL con Qiskit–Aer (simulación ideal), ruido simulado (modelo del dispositivo) y QPU real de IBM Quantum.  

Se comparan los pagos esperados de Alice y Bob para 31 grados de entrelazamiento γ ∈ [0, π], evaluando desviaciones teóricas y prácticas en plataformas NISQ.

---

## Requisitos

- Python ≥ 3.8  
- Qiskit 2.0.1  
- Qiskit-Aer 0.17.0  
- Qiskit-IBM-Runtime 0.39.0  
- NumPy, Matplotlib, NetworkX  

---

## Instalación

```bash
# Crear y activar un entorno virtual (opcional pero recomendado)
python -m venv venv
source venv/bin/activate  # Linux/macOS
venv\Scripts\activate     # Windows

# Instalar dependencias
pip install -U -c https://qisk.it/1-0-constraints \
    qiskit==2.0.1 \
    qiskit-aer==0.17.0 \
    qiskit-ibm-runtime==0.39.0 \
    numpy matplotlib networkx
