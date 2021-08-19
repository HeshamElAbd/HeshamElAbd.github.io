---
layout: post
title: "Three months of Oxidizing Code"
date: 2021-06-21 23:06:00 +5230
categories: Rust 
---
Almost three months ago I started coding in Rust and since then, I have  fallen in love with the language. If you used to code in C/C++, most likely, you would love it too. To give more context to the story I think it will make more sense to tell you why I switched to it in the first place. So, the story started years ago while I was mainly coding in C++ and Python. The combination was sweet, I mainly used Python for scripting and non-performance critical stuff and C++ for the heavy lifting. Early this year, I had a heavy computational task where performance was a major bottle neck and hence I had to write the whole project end-2-end in C++. One of the major bottleneck was productivity, development in C++ is slow, compilation becomes slow as the project grows, memory-management becomes tricky, while managing dependencies becomes hell on earth. This period was full of frustration and pain, luckily, during this time I got acquaintance with Rust.  

The internet is full of articles about Rust history, however this post is not about that it is about why I love Rust. So, let's jump in ...

1- Rust is statically typed language with an amazing type-deduction 
{% highlight rust %}
fn main()
{
    let y:str="Hello world"; // adding type information
    let x="Hello world"; // rust deducing the type automatically
    assert_eq!(x,y)
}

2- Cosies and clear syntax using iterators
{% highlight rust %}
fn main()
{
    let test_code=vec![1,2,3,4,5,6,7,8,9].iter()
                .filter(|num| num%2==0)
                .map(|num| num*num)
                .sum::<i32>();
    println!("The sum of square for even numbers is : {}",test_code); 
}

3- Out of the box support for parallel coding using Ray  

{% highlight rust %}
use rayon::prelude::*
fn main()
{
    let test_code=vec![1,2,3,4,5,6,7,8,9].par_iter()
                .map(|num| num*num)
                .collect::<Vec<i32>>();
    println!("The resulting vector is : {}",test_code);
}

4- Build-in support for unit testing

{% highlight rust %}
use rayon::prelude::*

fn add_one(vec_int:&mut Vec<String>)
{
    for e in vec_int.iter_mut()
    {
        *e+=1
    }
}

fn main()
{
    let test_code=vec![1,2,3,4,5,6,7,8,9];
    add_one(test_code);
    println!("The resulting vector is : {}",test_code);
}

#[cfg(test)]
mod unit_testing
{
    fn test_add_one()
    {
        let test_case=vec![1,2,3,4,5];
        let test_case_copy=test_case.clone();
        let test_res=add_one(&mut test_case_copy);
        for idx in 0..test_case.len()
        {
            assert_eq!(test_case[idx]+1,test_res[idx])
        }
    }
}

AS I am still learning and discovering more features in language I might come back to edit the post. 