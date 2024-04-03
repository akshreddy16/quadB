# quadB
fn is_palindrome(s: &str) -> bool {
    let reversed = s.chars().rev().collect::<String>();
    s == reversed
}

fn main() {
    let s = "racecar";
    println!("Is '{}' a palindrome? {}", s, is_palindrome(s));
}
fn first_occurrence(nums: &[i32], target: i32) -> Option<usize> {
    nums.iter().position(|&x| x == target)
}

fn main() {
    let nums = [1, 2, 3, 4, 5];
    let target = 3;
    println!("Index of first occurrence of {}: {:?}", target, first_occurrence(&nums, target));
}
fn is_prime(n: u64) -> bool {
    if n <= 1 {
        return false;
    }
    for i in 2..=n / 2 {
        if n % i == 0 {
            return false;
        }
    }
    true
}

fn main() {
    let num = 17;
    println!("Is {} prime? {}", num, is_prime(num));
}
fn median(nums: &[i32]) -> f64 {
    let len = nums.len();
    if len % 2 == 0 {
        (nums[len / 2 - 1] + nums[len / 2]) as f64 / 2.0
    } else {
        nums[len / 2] as f64
    }
}

fn main() {
    let nums = [1, 2, 3, 4, 5];
    println!("Median: {}", median(&nums));
}
fn longest_common_prefix(strings: &[String]) -> String {
    if strings.is_empty() {
        return String::new();
    }
    let mut prefix = strings[0].clone();
    for s in strings.iter().skip(1) {
        prefix = prefix.chars()
            .zip(s.chars())
            .take_while(|&(c1, c2)| c1 == c2)
            .map(|(c, _)| c)
            .collect();
    }
    prefix
}

fn main() {
    let strings = vec!["flower".to_string(), "flow".to_string(), "flight".to_string()];
    println!("Longest Common Prefix: {}", longest_common_prefix(&strings));
}
fn kth_smallest(nums: &[i32], k: usize) -> Option<i32> {
    nums.iter().cloned().nth(k - 1)
}

fn main() {
    let nums = [1, 3, 5, 7, 9];
    let k = 3;
    println!("{}th smallest element: {:?}", k, kth_smallest(&nums, k));
}
use std::cmp;

struct TreeNode {
    val: i32,
    left: Option<Box<TreeNode>>,
    right: Option<Box<TreeNode>>,
}

fn max_depth(root: Option<&Box<TreeNode>>) -> i32 {
    match root {
        Some(node) => {
            let left_depth = max_depth(node.left.as_ref());
            let right_depth = max_depth(node.right.as_ref());
            cmp::max(left_depth, right_depth) + 1
        }
        None => 0,
    }
}

fn main() {
    let root = Some(Box::new(TreeNode {
        val: 3,
        left: Some(Box::new(TreeNode {
            val: 9,
            left: None,
            right: None,
        })),
        right: Some(Box::new(TreeNode {
            val: 20,
            left: Some(Box::new(TreeNode {
                val: 15,
                left: None,
                right: None,
            })),
            right: Some(Box::new(TreeNode {
                val: 7,
                left: None,
                right: None,
            })),
        })),
    }));
    println!("Max Depth: {}", max_depth(root.as_ref()));
}
fn reverse_string(s: &str) -> String {
    s.chars().rev().collect()
}

fn main() {
    let s = "Hello, world!";
    println!("Reversed string: {}", reverse_string(s));
}
fn is_prime(n: u64) -> bool {
    if n <= 1 {
        return false;
    }
    for i in 2..=n / 2 {
        if n % i == 0 {
            return false;
        }
    }
    true
}

fn main() {
    let num = 17;
    println!("Is {} prime? {}", num, is_prime(num));
}
fn merge_sorted_arrays(arr1: &[i32], arr2: &[i32]) -> Vec<i32> {
    let mut result = Vec::with_capacity(arr1.len() + arr2.len());
    let mut i = 0;
    let mut j = 0;

    while i < arr1.len() && j < arr2.len() {
        if arr1[i] < arr2[j] {
            result.push(arr1[i]);
            i += 1;
        } else {
            result.push(arr2[j]);
            j += 1;
        }
    }

    while i < arr1.len() {
        result.push(arr1[i]);
        i += 1;
    }

    while j < arr2.len() {
        result.push(arr2[j]);
        j += 1;
    }

    result
}

fn main() {
    let arr1 = [1, 3, 5, 7];
    let arr2 = [2, 4, 6, 8];
    println!("Merged sorted arrays: {:?}", merge_sorted_arrays(&arr1, &arr2));
}
fn max_subarray_sum(nums: &[i32]) -> i32 {
    let mut max_sum = nums[0];
    let mut current_sum = nums[0];

    for &num in nums.iter().skip(1) {
        current_sum = current_sum.max(num);
        max_sum = max_sum.max(current_sum);
    }

    max_sum
}

fn main() {
    let nums = [-2, 1, -3, 4, -1, 2, 1, -5, 4];
    println!("Maximum subarray sum
