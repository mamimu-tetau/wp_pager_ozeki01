# wp_pager_ozeki01
めっちゃ簡単・シンプルなページャー、汎用性◎

## php

```
    <div class="pagination">
      <?php global $wp_rewrite;
      $paginate_base = get_pagenum_link(1);
      if(strpos($paginate_base, '?') || ! $wp_rewrite->using_permalinks()){
        $paginate_format = '';
        $paginate_base = add_query_arg('paged','%#%');
      }
      else{
        $paginate_format = (substr($paginate_base,-1,1) == '/' ? '' : '/') .
          user_trailingslashit('page/%#%/','paged');;
        $paginate_base .= '%_%';
      }
      echo paginate_links(array(
        'base' => $paginate_base,
        'format' => $paginate_format,
        'total' => $wp_query->max_num_pages,
        'mid_size' => 4,
        'current' => ($paged ? $paged : 1),
        'prev_text' => '« 前へ',
        'next_text' => '次へ »',
      )); ?>
    </div>
```

## css

```
  .pagination{
    text-align: center;
    margin-bottom:15px;
    span,
    a{
      display: inline-block;
    }
  }
  a.page-numbers,
  .pagination .current{
    padding:5px 8px;
    margin:0 2px;
    text-decoration: none;
  }
  .pagination .current{
    opacity: 0.8;
  }
  ```
