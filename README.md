

🌊 Underwater Terrain Explorer
A hands‑on project for visualizing and exploring global ocean‑floor bathymetry using Python and GEBCO data.
📌 Overview
The Underwater Terrain Explorer is a Python‑based project that loads real global bathymetry data, slices specific geographic regions, and generates high‑quality visualizations of underwater terrain.
This project focuses on the Gulf of Mexico, using the GEBCO 2023 dataset to reveal seafloor structure, depth variation, and major bathymetric features.
It’s designed to be:
beginner‑friendly
scientifically accurate
cleanly organized
easy to extend

📁 Project Structure
underwater terrain explorer/
│
├── data/
│   └── raw/
│       └── GEBCO_2023.nc        # Global bathymetry dataset
│
├── outputs/
│   ├── gulf_bathymetry.png      # Saved visualization
│   ├── Figure_1.png             # Auto‑generated figures
│   └── Figure_2.png
│
└── README.md                    # Project documentation

🧭 What This Project Does
Loads global bathymetry data using xarray
Extracts a specific region using latitude/longitude slicing
Visualizes underwater terrain using matplotlib
Saves high‑resolution maps to the outputs/ folder
Adds context layers such as:
titles
axis labels
colorbars
gridlines
improved colormaps

🛠️ How to Run the Project
1. Open Terminal
Navigate into the project folder:
cd "underwater terrain explorer"
2. Start Python
python3
You should now see:
>>>
3. Run the visualization code
Python
import xarray as xr
import matplotlib.pyplot as plt

ds = xr.open_dataset("data/raw/GEBCO_2023.nc")

gulf = ds.sel(
    lat=slice(18, 31),
    lon=slice(-98, -80)
)

plt.figure(figsize=(10, 8))

plot = gulf['elevation'].plot(
    cmap="viridis",
    cbar_kwargs={"label": "Elevation (meters)"}
)

plt.title("Gulf of Mexico Bathymetry (GEBCO 2023)")
plt.xlabel("Longitude")
plt.ylabel("Latitude")
plt.grid(True, linestyle="--", alpha=0.4)

plt.show()
4. Save the figure
Python
plt.savefig("outputs/gulf_bathymetry.png", dpi=300)
Your map will appear in the outputs/ folder.

🌅 Example Output
gulf_bathymetry.png
A high‑resolution bathymetry map of the Gulf of Mexico, complete with:
labeled axes
colorbar
gridlines
clear title
ocean‑friendly colormap

🚀 Future Enhancements
Add coastline contours
Annotate major features (Sigsbee Deep, Mississippi Canyon, etc.)
Create multi‑panel comparison maps
Build a Python script (explore.py) to automate the workflow
Add support for user‑selected regions
Generate 3D terrain visualizations

💡 Why This Project Matters
This project demonstrates:
real geospatial data handling
scientific visualization
clean project organization
reproducible workflows
technical curiosity and exploration
It’s a strong foundation for more advanced oceanographic or geospatial analysis.

