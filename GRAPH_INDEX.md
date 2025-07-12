# Forest Fire Prediction System - Graph Index

## 📊 Quick Reference Guide to All Visualizations

This document provides a quick reference to all graphs and visualizations in the Forest Fire Prediction System, organized by category and purpose.

---

## 🎯 Graph Categories

### 1. **INPUT DATA VISUALIZATION**
*Purpose: Display raw environmental data for fire prediction*

| Graph Type | Purpose | Why Important | Code Location |
|------------|---------|---------------|---------------|
| **Temperature Map** | Show temperature distribution | High temp = high fire risk | `plt.imshow(temperature, cmap='Reds')` |
| **Humidity Map** | Show moisture levels | Low humidity = fire prone | `plt.imshow(humidity, cmap='Blues')` |
| **Wind Speed Map** | Show wind patterns | High wind = rapid spread | `plt.imshow(wind_speed, cmap='Greens')` |
| **Wind Direction Map** | Show wind direction | Predicts spread direction | `plt.imshow(wind_dir, cmap='plasma')` |
| **Rainfall Map** | Show precipitation | Low rain = dry conditions | `plt.imshow(rainfall, cmap='viridis')` |
| **Elevation Map (DEM)** | Show topography | Affects fire behavior | `plt.imshow(dem, cmap='terrain')` |
| **Land Use Map** | Show vegetation types | Different fire risks | `plt.imshow(lulc, cmap='tab10')` |
| **Roads Map** | Show infrastructure | Access and ignition sources | `plt.imshow(roads, cmap='copper')` |
| **Settlements Map** | Show human presence | Evacuation planning | `plt.imshow(settlements, cmap='cool')` |

### 2. **MODEL PREDICTION VISUALIZATION**
*Purpose: Show model results and predictions*

| Graph Type | Purpose | Why Important | Code Location |
|------------|---------|---------------|---------------|
| **Fire Labels Map** | Show actual fire locations | Ground truth validation | `plt.imshow(fire_labels, cmap='RdYlBu_r')` |
| **Fire Prediction Map** | Show binary predictions | Fire/no-fire decisions | `plt.imshow(prediction_map, cmap='RdYlBu_r')` |
| **Fire Probability Map** | Show fire likelihood (0-1) | Risk assessment | `plt.imshow(fire_probability_map, cmap='Reds')` |
| **Prediction vs Actual** | Compare predictions to reality | Model accuracy check | Side-by-side comparison |

### 3. **FIRE SPREAD SIMULATION**
*Purpose: Visualize fire evolution over time*

| Graph Type | Purpose | Why Important | Code Location |
|------------|---------|---------------|---------------|
| **1-Hour Spread** | Show immediate spread | Emergency response | `plt.imshow(spread_maps['1h'], cmap='RdYlBu_r')` |
| **2-Hour Spread** | Show early evolution | Containment decisions | `plt.imshow(spread_maps['2h'], cmap='RdYlBu_r')` |
| **3-Hour Spread** | Show pattern development | Strategy adjustment | `plt.imshow(spread_maps['3h'], cmap='RdYlBu_r')` |
| **6-Hour Spread** | Show extended impact | Resource allocation | `plt.imshow(spread_maps['6h'], cmap='RdYlBu_r')` |
| **12-Hour Spread** | Show long-term evolution | Evacuation planning | `plt.imshow(spread_maps['12h'], cmap='RdYlBu_r')` |
| **Spread Animation** | Show dynamic evolution | Training and education | `animation.FuncAnimation()` |

### 4. **MODEL PERFORMANCE ANALYSIS**
*Purpose: Evaluate model quality and reliability*

| Graph Type | Purpose | Why Important | Code Location |
|------------|---------|---------------|---------------|
| **Accuracy Bar Chart** | Show model performance | Operational reliability | `metrics_df.plot(kind='bar')` |
| **Feature Importance** | Show factor importance | Understanding drivers | `sns.barplot(importance_df)` |
| **Confusion Matrix** | Show prediction errors | Error analysis | `sns.heatmap(confusion_matrix)` |
| **ROC Curve** | Show sensitivity/specificity | Threshold optimization | `plt.plot(fpr, tpr)` |
| **Precision-Recall Curve** | Show trade-off analysis | Performance tuning | `plt.plot(recall, precision)` |

### 5. **CORRELATION ANALYSIS**
*Purpose: Understand relationships between factors*

| Graph Type | Purpose | Why Important | Code Location |
|------------|---------|---------------|---------------|
| **Correlation Matrix** | Show factor relationships | Feature selection | `sns.heatmap(correlation_matrix)` |
| **Fire vs No-Fire Conditions** | Compare environmental conditions | Model validation | `plt.hist([fire_data, no_fire_data])` |
| **Scatter Plots** | Show factor interactions | Pattern recognition | `plt.scatter(x, y, c=fire_labels)` |
| **Distribution Plots** | Show data distributions | Data quality check | `sns.histplot(data)` |

### 6. **SCENARIO ANALYSIS**
*Purpose: Compare different environmental conditions*

| Graph Type | Purpose | Why Important | Code Location |
|------------|---------|---------------|---------------|
| **Drought Scenario** | Show drought conditions | Extreme risk planning | Scenario comparison grid |
| **Windy Scenario** | Show high wind impact | Rapid spread planning | Scenario comparison grid |
| **Summer Scenario** | Show peak season risk | Seasonal planning | Scenario comparison grid |
| **Urban Interface** | Show WUI conditions | Community protection | Scenario comparison grid |
| **Scenario Comparison** | Compare all scenarios | Comprehensive planning | `plt.subplots(2, 2)` |

### 7. **COMPREHENSIVE DASHBOARDS**
*Purpose: Provide complete overview in single view*

| Graph Type | Purpose | Why Important | Code Location |
|------------|---------|---------------|---------------|
| **Multi-Panel Dashboard** | Show complete analysis | Executive reporting | `fig.add_gridspec(3, 4)` |
| **Results Summary** | Consolidate all outputs | Decision making | Final visualization cell |
| **Statistical Summary** | Show key metrics | Quick assessment | Statistics display |

---

## 🎨 Color Scheme Guide

### **Standard Color Mappings:**
- **Red (`'Reds'`, `'RdYlBu_r'`)**: Fire risk, temperature, danger levels
- **Blue (`'Blues'`)**: Humidity, water presence, safety levels
- **Green (`'Greens'`)**: Wind speed, vegetation, neutral data
- **Terrain (`'terrain'`)**: Elevation, topographic data
- **Plasma (`'plasma'`)**: Wind direction, continuous data
- **Viridis (`'viridis'`)**: Rainfall, scientific data
- **Tab10 (`'tab10'`)**: Categorical data (land use types)

### **Color Interpretation:**
- **Dark Red**: High risk, high values, immediate attention
- **Light Red**: Medium risk, moderate values, caution
- **White/Light**: Low risk, low values, normal conditions
- **Dark Blue**: High humidity, low fire risk, favorable conditions
- **Light Blue**: Low humidity, increased fire risk, watch conditions

---

## 📈 Graph Usage by Purpose

### **For Emergency Response:**
1. Fire Probability Map → Identify high-risk areas
2. Fire Spread Animation → Plan evacuation routes
3. 1-Hour Spread Map → Immediate response needs
4. Wind Speed/Direction → Predict spread direction

### **For Fire Prevention:**
1. Temperature Map → Monitor heat buildup
2. Humidity Map → Identify dry conditions
3. Feature Importance → Focus on key factors
4. Scenario Analysis → Plan for different conditions

### **For Resource Allocation:**
1. Fire Prediction Map → Deploy resources
2. 6-Hour Spread Map → Position equipment
3. Urban Interface Scenario → Protect communities
4. Model Performance → Trust assessment

### **For Research and Analysis:**
1. Correlation Matrix → Understand relationships
2. Fire vs No-Fire Conditions → Model validation
3. Feature Importance → Scientific insights
4. All Scenarios → Comprehensive understanding

---

## 🔧 Technical Implementation

### **Creating Custom Visualizations:**
```python
# Basic template for any fire-related visualization
def create_fire_visualization(data, title, save_path=None):
    fig, ax = plt.subplots(figsize=(10, 8))
    im = ax.imshow(data, cmap='Reds', interpolation='nearest')
    ax.set_title(title, fontsize=14, fontweight='bold')
    ax.axis('off')
    
    # Add colorbar
    cbar = plt.colorbar(im, ax=ax, shrink=0.8)
    cbar.set_label('Fire Risk Level', rotation=270, labelpad=20)
    
    # Save if path provided
    if save_path:
        plt.savefig(save_path, dpi=300, bbox_inches='tight')
    
    plt.show()
    return fig
```

### **Animation Creation:**
```python
# Template for creating spread animations
def create_spread_animation(spread_data, output_path):
    fig, ax = plt.subplots(figsize=(10, 8))
    
    def animate(frame):
        ax.clear()
        time_step = list(spread_data.keys())[frame]
        im = ax.imshow(spread_data[time_step], cmap='RdYlBu_r', vmin=0, vmax=1)
        ax.set_title(f'Fire Spread - {time_step}', fontsize=14)
        ax.axis('off')
        return [im]
    
    anim = animation.FuncAnimation(fig, animate, frames=len(spread_data), 
                                   interval=1000, blit=False, repeat=True)
    anim.save(output_path, writer='pillow', fps=1)
    return anim
```

---

## 📊 Visualization Checklist

### **Before Creating Graphs:**
- [ ] Understand the data type and range
- [ ] Choose appropriate color scheme
- [ ] Consider the target audience
- [ ] Plan for accessibility (color blind friendly)

### **Graph Quality Check:**
- [ ] Clear title and labels
- [ ] Appropriate scale and units
- [ ] Readable font sizes
- [ ] Proper color contrast
- [ ] Legend when needed

### **For Publications:**
- [ ] High resolution (300 DPI minimum)
- [ ] Vector format (PDF, SVG) when possible
- [ ] Clear caption explaining the graph
- [ ] Consistent style across all graphs

---

## 🎯 Best Practices

### **Do:**
- Use consistent color schemes across related graphs
- Provide clear legends and labels
- Choose appropriate scales for your data
- Test visualizations with stakeholders
- Export in multiple formats

### **Don't:**
- Use too many colors in one graph
- Make graphs too cluttered
- Ignore accessibility considerations
- Use misleading scales
- Forget to validate with domain experts

---

## 📱 Interactive Features

### **Planned Interactive Elements:**
- Hover tooltips showing exact values
- Zoom and pan capabilities
- Toggle layers on/off
- Time slider for animations
- Click for detailed information

### **Implementation Example:**
```python
# Using plotly for interactive maps
import plotly.express as px
import plotly.graph_objects as go

fig = px.imshow(fire_probability_map, 
                color_continuous_scale='Reds',
                title='Interactive Fire Probability Map')
fig.update_layout(
    title_font_size=16,
    coloraxis_colorbar=dict(title="Fire Probability")
)
fig.show()
```

---

## 🚀 Future Enhancements

### **Planned Visualizations:**
- 3D fire spread visualization
- Real-time updating dashboards
- Mobile-responsive graphs
- Augmented reality overlays
- Satellite imagery integration

### **Advanced Analytics:**
- Machine learning visualization
- Uncertainty quantification plots
- Sensitivity analysis charts
- Multi-model comparison views
- Historical trend analysis

---

**Quick Access Links:**
- [Main README](README.md)
- [Installation Guide](README.md#installation)
- [Usage Examples](README.md#usage)
- [Troubleshooting](README.md#troubleshooting)

**Last Updated**: July 2025
**Version**: 1.0
