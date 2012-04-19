#SUMMARY
#Search engine (Udacity contest CS101)

#!/usr/bin/env python
# coding: utf-8

# this code is provided under a CC BY-NC-SA license
# created on Apr 18, 2012
# @author: Alexey Krasov


result_sum = {} 
# example data_structure: {keyword : {url : price, url_1 : price_1, ... }, keyword_1 : {...}, ... }
def lookup(data_structure, keyword):                    
    result_lookup = {}
    if keyword in data_structure:
        result_lookup = data_structure[keyword]
        return result_lookup 
    else:
        print "Ups. Try again!"

def summary_lookup(result_lookup):
    new = {}
    if result_sum == {}: result_sum = result_lookup
    else:
        for url_sum, price_sum in result_sum.iteritems():
            for url, price in result_lookup.iteritems():
                if url_sum == url:
                    new[url_sum] = price_sum + price
        result_sum = new
    return result_sum
                    
def summary_rate(result_sum):
    rank = {}
    for url, price in result_sum.iteritems():
        if price in rank: rank[price].append(url)
        else: rank[price] = [url]
    return rank