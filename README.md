from thermo import Mixture
from chemicals import search_chemical

def calculate_activity_coeffs(compounds, mole_fractions, T=298.15):
    """
    Calculates activity coefficients using the COSMO-SAC model.
    Note: Requires sigma profile data for the specific chemicals.
    """
    # Initialize the mixture
    # COSMO-SAC is a common choice for predictive modeling without experimental data
    mixture = Mixture(compounds, zs=mole_fractions, T=T)
    
    # Calculate Activity Coefficients (gamma)
    gammas = mixture.gammas()
    
    print(f"Results at {T} K:")
    for i, compound in enumerate(compounds):
        print(f"  {compound}: γ = {gammas[i]:.4f}")
    
    return gammas

# Example: Ethanol-Water Mixture
compounds = ['ethanol', 'water']
mole_fractions = [0.5, 0.5]
calculate_activity_coeffs(compounds, mole_fractions)
