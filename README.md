# airgradient-outdoor-friendly
Friendly explanations of the numbers given by AirGradient outdoor sensors for Home Assistant.

<img width="416" alt="image" src="https://github.com/user-attachments/assets/8beab2be-9f34-440f-96ce-cca41061adb3">

Add these to your configuration.yaml or build a template sensor helper and add the value template for each.

No single source was used for these values because there does not seem to be one. This is a mix of European and US limits skewing to use the lower limits if possible, and is therefore only a rough estimate of exposure levels and should not be relied upon if you have respiratory problems. PM0.3 was sourced from [Purple Air](https://community.purpleair.com/t/raw-sensor-data-layers/156), and the rest were sourced from Research Gate articles.

If you find a better more consistent source please update these in an issue.

~Gord

```
  - platform: template
    sensors:
      o_1pst_voc_index_friendly:
        friendly_name: "Outdoor VOC friendly"
        value_template: >-
          {% set aqi = states('sensor.o_1pst_voc_index') | float %}
          {% if aqi <= 50 %} 
          Good
          {% elif 51 >= aqi <= 100 %}
          Moderate
          {% elif 101 >= aqi <= 150 %}
          Unhealthy for Sensitive Groups
          {% elif 151 >= aqi <= 200 %}
          Unhealthy
          {% elif 201 >= aqi <= 300 %}
          Very Unhealthy
          {% elif aqi > 300 %} 
          Hazardous
          {% endif %}

      o_1pst_pm0_3_friendly:
        friendly_name: "Outdoor PM0.3 friendly"
        value_template: >-
          {% set aqi = states('sensor.o_1pst_pm0_3') | float %}
          {% if aqi <= 1000 %} 
          Good
          {% elif 1001 >= aqi <= 5000 %}
          Moderate
          {% elif 5001 >= aqi <= 10000 %}
          Unhealthy for Sensitive Groups
          {% elif 10001 >= aqi <= 20000 %}
          Unhealthy
          {% elif 20001 >= aqi <= 30000 %}
          Very Unhealthy
          {% elif aqi > 30001 %} 
          Hazardous
          {% endif %}

      o_1pst_pm1_friendly:
        friendly_name: "Outdoor PM1 friendly"
        value_template: >-
          {% set aqi = states('sensor.o_1pst_pm1') | float %}
          {% if aqi <= 9 %} 
          Good
          {% elif 10 >= aqi <= 35 %}
          Moderate
          {% elif 36 >= aqi <= 55 %}
          Unhealthy for Sensitive Groups
          {% elif 56 >= aqi <= 125 %}
          Unhealthy
          {% elif 126 >= aqi <= 225 %}
          Very Unhealthy
          {% elif aqi > 226 %} 
          Hazardous
          {% endif %}

      o_1pst_pm2_5_friendly:
        friendly_name: "Outdoor PM2.5 friendly"
        value_template: >-
          {% set aqi = states('sensor.o_1pst_pm2_5') | float %}
          {% if aqi <= 9 %} 
          Good
          {% elif 10 >= aqi <= 35 %}
          Moderate
          {% elif 36 >= aqi <= 55 %}
          Unhealthy for Sensitive Groups
          {% elif 56 >= aqi <= 125 %}
          Unhealthy
          {% elif 126 >= aqi <= 225 %}
          Very Unhealthy
          {% elif aqi > 226 %} 
          Hazardous
          {% endif %}

      o_1pst_pm10_friendly:
        friendly_name: "Outdoor PM10 friendly"
        value_template: >-
          {% set aqi = states('sensor.o_1pst_pm10') | float %}
          {% if aqi <= 54 %} 
          Good
          {% elif 55 >= aqi <= 154 %}
          Moderate
          {% elif 155 >= aqi <= 254 %}
          Unhealthy for Sensitive Groups
          {% elif 255 >= aqi <= 354 %}
          Unhealthy
          {% elif 355 >= aqi <= 424 %}
          Very Unhealthy
          {% elif aqi > 425 %} 
          Hazardous
          {% endif %}

      o_1pst_nox_index_friendly:
        friendly_name: "Outdoor NOX friendly"
        value_template: >-
          {% set aqi = states('sensor.o_1pst_nox_index') | float %}
          {% if aqi <= 50 %} 
          Good
          {% elif 51 >= aqi <= 100 %}
          Moderate
          {% elif 101 >= aqi <= 150 %}
          Unhealthy for Sensitive Groups
          {% elif 151 >= aqi <= 200 %}
          Unhealthy
          {% elif 201 >= aqi <= 300 %}
          Very Unhealthy
          {% elif aqi > 300 %} 
          Hazardous
          {% endif %}

      o_1pst_carbon_dioxide_friendly:
        friendly_name: "Outdoor CO2 friendly"
        value_template: >-
          {% set aqi = states('sensor.o_1pst_carbon_dioxide') | float %}
          {% if aqi <= 800 %} 
          Good
          {% elif 801 >= aqi <= 1100 %}
          Moderate
          {% elif 1101 >= aqi <= 1500 %}
          Unhealthy for Sensitive Groups
          {% elif 1501 >= aqi <= 2000 %}
          Unhealthy
          {% elif 2001 >= aqi <= 3000 %}
          Very Unhealthy
          {% elif aqi > 3001 %} 
          Hazardous
          {% endif %}

```
