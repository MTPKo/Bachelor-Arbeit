## Bachelor Arbeit:
 
Redo and improve the LIVIVO's document classification

## Infos
| was | info |
| ------ | ------ |
| Dauer |12 Wochen  |
| Start | abklären |
| Gutachter | KUF |
| Betreuer | KUF, KLI |
|Arbeitszeit | ca 2 Tage |

## Klassen
- Medizin
- Ernährung
- Umweltwissenschaften
- Landwirtschaft

## roadmap
```mermaid
graph TD
    setup[PC setup, installation] --> data
    data[data harvesting -> Text Corpus] --> corpus_validation[Corpus validation]
    data -------> GR[Golden Record]

    
    corpus_validation --> full_title[full title]
    corpus_validation --> mesh_extract[MeSH extract]
    full_title --> topic_modelling[topic modelling]
    mesh_extract --> topic_modelling[topic modelling]
    full_title --> w2v-space
    mesh_extract --> w2v-space
    
    topic_modelling --> TFIDF[TF-IDF<br>term frequency - inverse document frequency] 
    topic_modelling --> LDA[LDA<br> Latent Dirichlet Allocation]

    w2v-space -->|optional: DIM reduction| unsupervised[unsupervised<br>KNN]
    w2v-space --> datasets[create train/test/validation datasets]
    datasets -->|optional: DIM reduction| trees[supervised<br>decision tree methods]

    trees --> Validation
    unsupervised --> Validation
    TFIDF --> Validation
    LDA --> Validation
    GR --> Validation

```

----

        



```mermaid
gantt
    title timeline
    dateFormat  YYYY-MM-DD
    axisFormat   %W-%y
    section Vorbereitung
        PC setup           :a1, 2023-01-01, 1w
        create Corpus      :a2, after a1, 2w    

    section unsupervised
        w2v                :a4, after a2,3w
        w2v-clustering : a7, after a6, 3w
    
    section supervised
        create Datasets       :a3, after a4, 1w
        w2v-classification :   a8, after a3, 2w        
    
    section topic modelling
        TFIDF      : a5, after a2, 10d
        LDA   : a6, after a5, 11d
        


        

    section Schreiben
        Schreiben      :after a8,3w
    
```

