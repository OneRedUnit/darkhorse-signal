# Пайплайн обработки

Connectors(IMAP/SES/API)

   → Fetcher
   
      → MIME Normalizer (HTML→text, PDF→text+OCR, IMG→OCR)
      
         → Signature & Dedup (content_id)
         
            → Source Canonicalizer (broker, analyst)
            
               → Ticker Mapper (NER→ticker map)
               
                  → Classifier (note_type: market|sector|stock, rec_type)
                  
                     → Extractor (rating/TP/horizon/key_bullets)
                     
                        → QA Guard (rules+LLM check)
                        
                           → Persist (DB + blob store)
                           
                              → Publish (NEXUS feed + Web index)

Ключевые блоки:

Connectors: IMAP (Gmail/Office365), AWS SES Inbound, SFTP/HTTP дропбоксы.

Normalizer: html2text, PDF‑парсинг + OCR, извлечение таблиц (tabula/camelot).

Dedup: content_hash = sha256(norm_text+attachments_meta), fuzzy‑match для повторов.

NER/Mapping: сущности → тикеры (словарь + regex + ISIN/CUSIP; разрешение конфликтов по контексту).

Classifier: письмо → market/sector/stock/other; для stock — recommendation: Buy/Hold/Sell/Init/Cover/Raise/Lower/No-Change.

Extractor: tp, ptp_delta, rating_prev→rating_new, coverage_init, risk_factors, thesis_bullets(<=5).

QA Guard: правила + короткая LLM‑проверка консистентности (без фантазии: “цитаты только из источника”).
Persist/Publish: RDBMS + blob‑хранилище; индексация полнотекста/векторов; JSON‑фиды для NEXUS.
