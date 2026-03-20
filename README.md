import numpy as np
import matplotlib.pyplot as plt
from matplotlib.colors import LinearSegmentedColormap

def create_heart(x, y, size):
    """Genereer x- en y-coördinaten voor een hartvorm."""
    t = np.linspace(0, 2 * np.pi, 1000)
    x_heart = 16 * np.sin(t) ** 3
    y_heart = 13 * np.cos(t) - 5 * np.cos(2 * t) - 2 * np.cos(3 * t) - np.cos(4 * t)
    
    x_heart = x + size * x_heart
    y_heart = y + size * y_heart
    return x_heart, y_heart

def main():
    # Maak een grote figuur
    plt.figure(figsize=(20, 20))
    
    # Kleurencombinatie voor het hartje
    colors = ['#FF0000', '#FF6666', '#FF9999', '#FFCCCC', '#FFFFFF']
    cmap = LinearSegmentedColormap.from_list('heart_cmap', colors, N=256)
    
    # Meerdere hartjes met verschillende grootte en positie
    for i in range(100):
        size = np.random.uniform(0.01, 0.05)
        x_pos = np.random.uniform(-1, 1)
        y_pos = np.random.uniform(-1, 1)
        
        x_heart, y_heart = create_heart(x_pos, y_pos, size)
        color = cmap(i / 100)
        
        plt.fill(x_heart, y_heart, color=color, alpha=np.random.uniform(0.5, 1))
    
    # Achtergrond en styling
    plt.gca().set_facecolor('#FFEBEE')
    plt.title("Extreem Groot en Uitgebreid Hartje", fontsize=24, color='#FF0000')
    plt.axis('off')
    plt.tight_layout()
    
    # Opslaan en tonen
    plt.savefig('hartje.png', dpi=300, bbox_inches='tight')
    plt.show()

if __name__ == "__main__":
    main()
