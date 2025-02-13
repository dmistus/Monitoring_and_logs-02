# «Средство визуализации Grafana»

## Задание 1

### *1.	Используя директорию help внутри этого домашнего задания, запустите связку prometheus-grafana.*

2.	Зайдите в веб-интерфейс grafana, используя авторизационные данные, указанные в манифесте docker-compose.
3.	Подключите поднятый вами prometheus, как источник данных.
4.	Решение домашнего задания — скриншот веб-интерфейса grafana со списком подключенных Datasource.

![](img/1.png)


## Задание 2

### *Для решения этого задания приведите promql-запросы для выдачи этих метрик, а также скриншот получившейся Dashboard.*

Создайте Dashboard и в ней создайте Panels:

Утилизация CPU для nodeexporter (в процентах, 100-idle);
 
```
avg without (cpu)(irate(node_cpu_seconds_total{job="nodeexporter",mode="idle"}[1m])) * 100
```

![](img/2.png)


CPULA 1/5/15;


```
avg(node_load1{job="node-exporter"})
avg(node_load5{job="node-exporter"})
avg(node_load15{job="node-exporter"})
```


![](img/3.png)

Kоличество свободной оперативной памяти;

```
node_memory_MemFree_bytes
```

![](img/4.png)

Kоличество места на файловой системе.

```
node_filesystem_avail_bytes
```

![](img/5.png)

### Задание 3

### *1.	Создайте для каждой Dashboard подходящее правило alert — можно обратиться к первой лекции в блоке «Мониторинг».2.	В качестве решения задания приведите скриншот вашей итоговой Dashboard*


![](img/6.png)

## Задание 4

1.	Сохраните ваш Dashboard.Для этого перейдите в настройки Dashboard, выберите в боковом меню «JSON MODEL». Далее скопируйте отображаемое json-содержимое в отдельный файл и сохраните его.
2.	В качестве решения задания приведите листинг этого файла.


```
{
  "annotations": {
    "list": [
      {
        "builtIn": 1,
        "datasource": {
          "type": "grafana",
          "uid": "-- Grafana --"
        },
        "enable": true,
        "hide": true,
        "iconColor": "rgba(0, 211, 255, 1)",
        "name": "Annotations & Alerts",
        "type": "dashboard"
      }
    ]
  },
  "editable": true,
  "fiscalYearStartMonth": 0,
  "graphTooltip": 0,
  "id": 1,
  "links": [],
  "liveNow": false,
  "panels": [
    {
      "datasource": {
        "type": "prometheus",
        "uid": "aff9f1de-cc2f-4ccf-87a0-9081e4874060"
      },
      "fieldConfig": {
        "defaults": {
          "color": {
            "mode": "palette-classic"
          },
          "custom": {
            "axisBorderShow": false,
            "axisCenteredZero": false,
            "axisColorMode": "text",
            "axisLabel": "",
            "axisPlacement": "auto",
            "barAlignment": 0,
            "drawStyle": "line",
            "fillOpacity": 0,
            "gradientMode": "none",
            "hideFrom": {
              "legend": false,
              "tooltip": false,
              "viz": false
            },
            "insertNulls": false,
            "lineInterpolation": "linear",
            "lineWidth": 1,
            "pointSize": 5,
            "scaleDistribution": {
              "type": "linear"
            },
            "showPoints": "auto",
            "spanNulls": false,
            "stacking": {
              "group": "A",
              "mode": "none"
            },
            "thresholdsStyle": {
              "mode": "off"
            }
          },
          "mappings": [],
          "thresholds": {
            "mode": "absolute",
            "steps": [
              {
                "color": "green",
                "value": null
              },
              {
                "color": "red",
                "value": 80
              }
            ]
          }
        },
        "overrides": []
      },
      "gridPos": {
        "h": 9,
        "w": 9,
        "x": 0,
        "y": 0
      },
      "id": 1,
      "options": {
        "legend": {
          "calcs": [],
          "displayMode": "list",
          "placement": "bottom",
          "showLegend": true
        },
        "tooltip": {
          "mode": "single",
          "sort": "none"
        }
      },
      "targets": [
        {
          "datasource": {
            "type": "prometheus",
            "uid": "aff9f1de-cc2f-4ccf-87a0-9081e4874060"
          },
          "editorMode": "code",
          "expr": "100 - avg(irate(node_cpu_seconds_total{job=\"node-exporter\", mode=\"idle\"}[1m])) * 100",
          "instant": false,
          "legendFormat": "Утилизация CPU (в процентах, 100-idle)",
          "range": true,
          "refId": "A"
        }
      ],
      "title": "Утилизация CPU (в процентах, 100-idle)",
      "type": "timeseries"
    },
    {
      "datasource": {
        "type": "prometheus",
        "uid": "aff9f1de-cc2f-4ccf-87a0-9081e4874060"
      },
      "fieldConfig": {
        "defaults": {
          "color": {
            "mode": "palette-classic"
          },
          "custom": {
            "axisBorderShow": false,
            "axisCenteredZero": false,
            "axisColorMode": "text",
            "axisLabel": "",
            "axisPlacement": "auto",
            "barAlignment": 0,
            "drawStyle": "line",
            "fillOpacity": 0,
            "gradientMode": "none",
            "hideFrom": {
              "legend": false,
              "tooltip": false,
              "viz": false
            },
            "insertNulls": false,
            "lineInterpolation": "linear",
            "lineWidth": 1,
            "pointSize": 5,
            "scaleDistribution": {
              "type": "linear"
            },
            "showPoints": "auto",
            "spanNulls": false,
            "stacking": {
              "group": "A",
              "mode": "none"
            },
            "thresholdsStyle": {
              "mode": "off"
            }
          },
          "mappings": [],
          "thresholds": {
            "mode": "absolute",
            "steps": [
              {
                "color": "green",
                "value": null
              },
              {
                "color": "red",
                "value": 80
              }
            ]
          }
        },
        "overrides": []
      },
      "gridPos": {
        "h": 9,
        "w": 10,
        "x": 9,
        "y": 0
      },
      "id": 2,
      "options": {
        "legend": {
          "calcs": [],
          "displayMode": "list",
          "placement": "bottom",
          "showLegend": true
        },
        "tooltip": {
          "mode": "single",
          "sort": "none"
        }
      },
      "targets": [
        {
          "datasource": {
            "type": "prometheus",
            "uid": "aff9f1de-cc2f-4ccf-87a0-9081e4874060"
          },
          "editorMode": "code",
          "expr": "avg(node_load1{job=\"node-exporter\"})",
          "instant": false,
          "legendFormat": "Средняя нагрузка на процессор за последнюю 1 минуту",
          "range": true,
          "refId": "A"
        },
        {
          "datasource": {
            "type": "prometheus",
            "uid": "aff9f1de-cc2f-4ccf-87a0-9081e4874060"
          },
          "editorMode": "code",
          "expr": "avg(node_load5{job=\"node-exporter\"})",
          "hide": false,
          "instant": false,
          "legendFormat": "Средняя нагрузка на процессор за последние 5 минут",
          "range": true,
          "refId": "B"
        },
        {
          "datasource": {
            "type": "prometheus",
            "uid": "aff9f1de-cc2f-4ccf-87a0-9081e4874060"
          },
          "editorMode": "code",
          "expr": "avg(node_load15{job=\"node-exporter\"})",
          "hide": false,
          "instant": false,
          "legendFormat": "Средняя нагрузка на процессор за последние 15 минут",
          "range": true,
          "refId": "C"
        }
      ],
      "title": "Средняя нагрузка на процессор",
      "type": "timeseries"
    },
    {
      "datasource": {
        "type": "prometheus",
        "uid": "aff9f1de-cc2f-4ccf-87a0-9081e4874060"
      },
      "fieldConfig": {
        "defaults": {
          "color": {
            "mode": "palette-classic"
          },
          "custom": {
            "axisBorderShow": false,
            "axisCenteredZero": false,
            "axisColorMode": "text",
            "axisLabel": "",
            "axisPlacement": "auto",
            "barAlignment": 0,
            "drawStyle": "line",
            "fillOpacity": 0,
            "gradientMode": "none",
            "hideFrom": {
              "legend": false,
              "tooltip": false,
              "viz": false
            },
            "insertNulls": false,
            "lineInterpolation": "linear",
            "lineWidth": 1,
            "pointSize": 5,
            "scaleDistribution": {
              "type": "linear"
            },
            "showPoints": "auto",
            "spanNulls": false,
            "stacking": {
              "group": "A",
              "mode": "none"
            },
            "thresholdsStyle": {
              "mode": "off"
            }
          },
          "mappings": [],
          "thresholds": {
            "mode": "absolute",
            "steps": [
              {
                "color": "green",
                "value": null
              },
              {
                "color": "red",
                "value": 80
              }
            ]
          },
          "unit": "decbytes"
        },
        "overrides": []
      },
      "gridPos": {
        "h": 9,
        "w": 9,
        "x": 0,
        "y": 9
      },
      "id": 3,
      "options": {
        "legend": {
          "calcs": [],
          "displayMode": "list",
          "placement": "bottom",
          "showLegend": true
        },
        "tooltip": {
          "mode": "single",
          "sort": "none"
        }
      },
      "targets": [
        {
          "datasource": {
            "type": "prometheus",
            "uid": "aff9f1de-cc2f-4ccf-87a0-9081e4874060"
          },
          "editorMode": "code",
          "expr": "node_memory_MemTotal_bytes",
          "instant": false,
          "legendFormat": "Общее количество оперативной памяти",
          "range": true,
          "refId": "A"
        },
        {
          "datasource": {
            "type": "prometheus",
            "uid": "aff9f1de-cc2f-4ccf-87a0-9081e4874060"
          },
          "editorMode": "code",
          "expr": "node_memory_MemFree_bytes",
          "hide": false,
          "instant": false,
          "legendFormat": "Количество свободной  оперативной памяти",
          "range": true,
          "refId": "B"
        }
      ],
      "title": "Оперативная память",
      "type": "timeseries"
    },
    {
      "datasource": {
        "type": "prometheus",
        "uid": "aff9f1de-cc2f-4ccf-87a0-9081e4874060"
      },
      "fieldConfig": {
        "defaults": {
          "color": {
            "mode": "palette-classic"
          },
          "custom": {
            "axisBorderShow": false,
            "axisCenteredZero": false,
            "axisColorMode": "text",
            "axisLabel": "",
            "axisPlacement": "auto",
            "barAlignment": 0,
            "drawStyle": "line",
            "fillOpacity": 0,
            "gradientMode": "none",
            "hideFrom": {
              "legend": false,
              "tooltip": false,
              "viz": false
            },
            "insertNulls": false,
            "lineInterpolation": "linear",
            "lineWidth": 1,
            "pointSize": 5,
            "scaleDistribution": {
              "type": "linear"
            },
            "showPoints": "auto",
            "spanNulls": false,
            "stacking": {
              "group": "A",
              "mode": "none"
            },
            "thresholdsStyle": {
              "mode": "off"
            }
          },
          "mappings": [],
          "thresholds": {
            "mode": "absolute",
            "steps": [
              {
                "color": "green",
                "value": null
              },
              {
                "color": "red",
                "value": 80
              }
            ]
          },
          "unit": "decbytes"
        },
        "overrides": []
      },
      "gridPos": {
        "h": 9,
        "w": 10,
        "x": 9,
        "y": 9
      },
      "id": 4,
      "options": {
        "legend": {
          "calcs": [],
          "displayMode": "list",
          "placement": "bottom",
          "showLegend": true
        },
        "tooltip": {
          "mode": "single",
          "sort": "none"
        }
      },
      "pluginVersion": "10.2.3",
      "targets": [
        {
          "datasource": {
            "type": "prometheus",
            "uid": "aff9f1de-cc2f-4ccf-87a0-9081e4874060"
          },
          "editorMode": "code",
          "expr": "node_filesystem_avail_bytes",
          "instant": false,
          "legendFormat": "__auto",
          "range": true,
          "refId": "A"
        }
      ],
      "title": "Количество места на файловой системе",
      "type": "timeseries"
    }
  ],
  "refresh": "",
  "schemaVersion": 39,
  "tags": [],
  "templating": {
    "list": []
  },
  "time": {
    "from": "now-30m",
    "to": "now"
  },
  "timepicker": {},
  "timezone": "",
  "title": "Local monitoring",
  "uid": "a028b9d9-0cab-4f10-9bb7-5e59829d3401",
  "version": 1,
  "weekStart": ""
}
```