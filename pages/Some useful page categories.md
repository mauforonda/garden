- ## Exploration logs
	- {{query (page-tags exploration dataset)}}
	  query-properties:: [:page]
- ## Data visualizations
	- {{query (page-tags dataviz)}}
	  query-properties:: [:page]
	  query-sort-by:: page
	  query-sort-desc:: true
- ## Article notes
	- {{query (and (page-tags Article) ) }}
	  query-table:: true
	  query-properties:: [:page]
- ## Notes from audio content
	- {{query (page-tags Audio) }}
	  query-properties:: [:page]